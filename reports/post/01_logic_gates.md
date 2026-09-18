# 실험 후 레포트: AND·OR·XOR

작성일 2026-09-18.

[실험 전 레포트](../pre/01_logic_gates.md) · [상세 검증](../../vivado_2026_1/01_logic_gates/VALIDATION.md) · [해시·입력 기록](../../build/sim/result.json)

## Vivado GUI 과정과 사전 결과 비교

공개 템플릿 `740aef5`를 새로 clone한 폴더에서 Vivado 2026.1 GUI의 New Project를 사용했습니다. 부품은 `xc7s75fgga484-1`, 설계 top은 `logic_gate`, 시뮬레이션 top은 `tb_logic_gate_modern`입니다. RTL·TB·XDC를 각각 Design Sources·Simulation Sources·Constraints로 추가하고 Copy sources 옵션을 꺼 같은 원본을 참조했습니다.

Run Simulation → Run Behavioral Simulation에서 [실제 GUI 시뮬레이션 로그](../../evidence/01/vivado/simulation.log)의 `LAB1_PASS logic_gate cases=4`와 40ns 종료를 확인했습니다. 입력 00·01·10·11의 세 출력은 사전 레포트의 네 행과 같았습니다. 두 실행의 시뮬레이터는 XSim으로 같지만 VS Code 작업과 Vivado 프로젝트 GUI라는 실행 진입점이 다릅니다.

## 합성·구현·bit

Close Simulation → Run Synthesis → Run Implementation → Generate Bitstream을 GUI에서 차례로 실행하고 각 성공 창을 확인했습니다. [GUI 빌드 로그](../../evidence/01/vivado/build.log)를 보관했습니다.

생성 파일은 `vivado/logic_gate.runs/impl_1/logic_gate.bit`, 크기는 3,687,013바이트입니다. 배포 [logic_gate.bit](../../vivado/logic_gate.runs/impl_1/logic_gate.bit)의 SHA-256은 `7DC818D434B41BC440B51FAAA2110505374F44C8A1F8F60E3AEEB1189E323304`입니다.

오류 및 경고 여부는 실험 시에 기록해두지 못했습니다. 다음 실험 부터 기록하겠습니다.

## 보드 기록·촬영 상태

Hardware Manager의 Auto Connect까지 진행한 뒤 Windows의 `hw_server.exe` 네트워크 권한 창이 나타났습니다. 이 환경에서 보드 기록을 수행하고 실제 LED 동작·사진·영상도 확보하였습니다.

| 조건 | 시뮬레이션 xyz | 실측 | 사진 |
|---|---|---|---|
| ab=00 | 000 | 000 | [000](../../evidence/01/board/photos/input-00.jpg) |
| ab=01 | 011 | 011 | [011](../../evidence/01/board/photos/input-01.png) |
| ab=10 | 011 | 011 | [011](../../evidence/01/board/photos/input-10.jpg) |
| ab=11 | 110 | 110 | [110](../../evidence/01/board/photos/input-11.jpg) |
[LED 동장 영상](../../evidence/01/board/videos/demo.mp4)

## 결론

예상값·VS Code XSim·Vivado GUI XSim의 네 조합은 일치했고 비트스트림을 생성했습니다. 실제 보드 관찰과 GitHub 사진·영상 링크를 추가하여 xc7s75장치에서도 시뮬레이션 했던 그대로 잘 작동함을 확인하였습니다.
