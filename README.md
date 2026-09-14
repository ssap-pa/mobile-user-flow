# Mobile User Flow

토스 Android 앱에서 관찰한 사용자 동선 패턴을 다양한 업종의 모바일 앱·모바일 웹 설계에 적용하는 스킬입니다. Claude Code와 Codex에서 같은 스킬 폴더를 그대로 사용합니다.

## 무엇을 하나요?

- 핵심 작업에 맞춘 정보 구조와 화면 간 이동 설계
- 점진적 입력, 최근 대상 활용, 요약 → 목록 → 상세 패턴 적용
- 버튼 동작, 뒤로 가기, 입력 보존, 빈 화면과 오류 처리 명세
- 예약·교육·현장 업무·커뮤니티 등 도메인별 적용
- 직접 관찰한 사실과 새로운 설계 제안 구분

토스 접속이나 휴대폰 연결 없이 사용할 수 있습니다. 특정 프레임워크나 토스의 시각 디자인을 강제하지 않습니다.

## 설치

저장소를 내려받습니다.

```sh
git clone https://github.com/ssap-pa/mobile-user-flow.git
```

### Claude Code

저장소 안의 `mobile-user-flow` 폴더를 스킬 디렉터리에 복사합니다.

- 모든 프로젝트에서 쓰려면 개인 스킬로 설치합니다.

  ```sh
  mkdir -p ~/.claude/skills
  cp -R mobile-user-flow/mobile-user-flow ~/.claude/skills/mobile-user-flow
  ```

- 특정 저장소에서만 쓰고 팀과 공유하려면 프로젝트 스킬로 설치합니다.

  ```sh
  mkdir -p <프로젝트>/.claude/skills
  cp -R mobile-user-flow/mobile-user-flow <프로젝트>/.claude/skills/mobile-user-flow
  ```

최종 구조가 `skills/mobile-user-flow/SKILL.md`인지 확인한 뒤 Claude Code를 다시 시작합니다. `/mobile-user-flow`로 직접 호출하거나, 아래처럼 요청하면 SKILL.md의 `description`에 따라 자동으로 사용됩니다.

```text
/mobile-user-flow 예약 앱의 전체 동선과 화면을 설계해줘.
예약 앱의 사용자 동선과 화면 구성을 설계해줘.
```

`agents/openai.yaml`은 Codex 전용 파일이며 Claude Code는 읽지 않습니다. 함께 복사해도 동작에 영향이 없습니다.

### Codex

저장소 안의 `mobile-user-flow` 폴더를 Codex 개인 스킬 폴더에 복사합니다. 기본 위치는 `~/.codex/skills/`이며, `CODEX_HOME`을 별도로 설정했다면 그 아래의 `skills/`를 사용합니다. 같은 이름의 스킬이 이미 있다면 기존 내용을 먼저 비교하세요.

```sh
mkdir -p ~/.codex/skills
cp -R mobile-user-flow/mobile-user-flow ~/.codex/skills/mobile-user-flow
```

최종 구조가 `skills/mobile-user-flow/SKILL.md`인지 확인합니다. Codex에서 새 대화를 열어 아래처럼 요청합니다.

```text
$mobile-user-flow로 예약 앱의 전체 동선과 화면을 설계해줘.
```

### 공통 예시

```text
교육 앱의 이어 학습과 학습 완료 후 동선을 설계해줘.
현재 프로젝트의 검색 → 목록 → 상세 → 신청 흐름을 개선하고 구현해줘.
```

## 구성

| 파일 | 용도 |
|---|---|
| [SKILL.md](mobile-user-flow/SKILL.md) | 스킬 진입점과 설계 지침 |
| [patterns.md](mobile-user-flow/references/patterns.md) | 패턴 선택표와 업종별 예시 |
| [flow-spec.md](mobile-user-flow/references/flow-spec.md) | 화면·전이·검증 명세 형식 |
| [toss-observations.md](mobile-user-flow/references/toss-observations.md) | 관찰한 토스 경로와 미확인 범위 |
| [openai.yaml](mobile-user-flow/agents/openai.yaml) | Codex 표시 정보와 호출 설정 (Codex 전용) |

## 자료 범위

2026년 9월 Android 토스 5.276.0에서 확인한 일부 경로에 기반합니다. 송금·결제·투자 실행 완료나 앱 전체 동선을 검증한 자료가 아니며, 패턴의 전환율 개선 효과를 측정하지 않았습니다.

배포 자료에는 원본 화면 캡처, 대화 기록, 개인 프로필, 계좌·거래 값, 연락처·주소, 기기 식별자, 로컬 사용자 경로, 인증 정보를 포함하지 않습니다. 문서에는 화면 구조와 일반화한 설계 지침만 담았습니다.

토스, OpenAI, Anthropic의 공식 배포물이 아니며 제휴 관계를 나타내지 않습니다. 상표와 서비스 이름은 관찰 대상을 설명하기 위해 사용합니다.

## 라이선스

이 저장소의 스킬 문서와 예시는 [MIT License](LICENSE)로 공유합니다.
