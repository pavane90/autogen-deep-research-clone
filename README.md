# autogen-deep-research-clone

Microsoft AutoGen을 활용한 멀티 에이전트 기반 이메일 최적화 시스템

## 프로젝트 개요

이 프로젝트는 Microsoft AutoGen 프레임워크를 사용하여 이메일 작성 및 최적화를 위한 협업 AI 에이전트 시스템을 구현합니다. 5개의 전문화된 에이전트가 라운드 로빈 방식으로 협력하여 이메일의 명확성, 톤, 설득력을 개선합니다.

### 주요 기능

- **ClarityAgent**: 명확성과 간결함에 집중, 모호성과 중복 제거
- **ToneAgent**: 감정적 톤과 전문성 조정, 따뜻하고 자신감 있는 표현
- **PersuasionAgent**: 설득력 향상, CTA 개선, 행동 심리학 기반 최적화
- **SynthesizerAgent**: 모든 에이전트의 제안을 통합하여 통일된 초안 작성
- **CriticAgent**: 최종 품질 평가 및 전문성 기준 충족 여부 판단

### 추가 도구

- **web_search_tool**: Firecrawl API를 사용한 웹 검색 및 콘텐츠 스크래핑 기능

## 요구사항

- Python 3.13 이상
- OpenAI API 키
- Firecrawl API 키 (웹 검색 기능 사용 시)

## 설치

1. 저장소 클론
```bash
git clone <repository-url>
cd autogen-deep-research-clone
```

2. 가상 환경 생성 및 활성화
```bash
python -m venv .venv
source .venv/bin/activate  # Mac/Linux
# .venv\Scripts\activate  # Windows
```

3. 의존성 설치 (uv 사용)
```bash
uv pip install -e .
```

또는 pip 사용:
```bash
pip install -e .
```

4. 개발 도구 설치 (Jupyter 노트북 실행 시)
```bash
uv pip install -e ".[dev]"
```

## 환경 설정

프로젝트 루트에 `.env` 파일을 생성하고 다음 API 키를 추가합니다:

```env
OPENAI_API_KEY=your_openai_api_key_here
FIRECRAWL_API_KEY=your_firecrawl_api_key_here
```

## 실행 방법

### Jupyter 노트북 실행

1. Jupyter Notebook 실행:
```bash
jupyter notebook email-optimizer-team.ipynb
```

2. 노트북에서 셀을 순차적으로 실행
3. 마지막 셀에서 최적화할 이메일 텍스트를 입력하여 실행

### Python 스크립트로 실행

tools.py의 웹 검색 기능을 사용하려면:

```python
from tools import web_search_tool

results = web_search_tool("your search query")
print(results)
```

## 프로젝트 구조

```
.
├── email-optimizer-team.ipynb  # 이메일 최적화 에이전트 팀 구현
├── tools.py                     # 웹 검색 도구 (Firecrawl)
├── pyproject.toml              # 프로젝트 의존성 및 설정
├── .env                        # API 키 (git에서 제외됨)
└── README.md                   # 프로젝트 문서
```

## 의존성

- `autogen>=0.9.7`: Microsoft AutoGen 프레임워크
- `autogen-agentchat>=0.7.2`: 에이전트 채팅 기능
- `autogen-ext[openai]>=0.7.2`: OpenAI 모델 지원
- `firecrawl-py==2.16.5`: 웹 스크래핑 및 검색
- `python-dotenv>=1.1.1`: 환경 변수 관리

## 사용 예시

노트북의 마지막 셀에서:

```python
await Console(
    team.run_stream(
        task="작성하거나 개선할 이메일 내용을 여기에 입력"
    )
)
```

에이전트 팀이 순차적으로 이메일을 분석하고 개선하여 최종적으로 전문적인 이메일을 생성합니다.
