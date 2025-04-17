

---

#  Hybrid Multi-Cloud Infrastructure with WireGuard, Kubernetes & Argo CD

> 로컬 VM ↔ Oracle Cloud 연동 기반 VPC 구성 및 GitOps 기반 클러스터 환경 구축

---

## 프로젝트 개요

이 프로젝트는 로컬 환경(Multipass 기반 VM 3대)과 Oracle Cloud를 WireGuard VPN으로 연결하여 하나의 통합 네트워크(VPC)를 구성하고, 그 위에 Kubernetes 클러스터 및 GitOps 기반 배포 시스템(Argo CD)을 구축한 실습 기반 인프라 프로젝트입니다.

---

##  사용 기술 스택

| 분류       | 기술 스택                                  |
|------------|---------------------------------------------|
| 가상화     | Multipass, Ubuntu 22.04                     |
| 네트워크   | WireGuard (VPN), VPC 구성                   |
| 클라우드   | Oracle Cloud Infrastructure (OCI)           |
| 클러스터   | Kubernetes (kubeadm)                        |
| 배포 자동화| Argo CD, GitHub (GitOps 기반 배포 자동화)    |
| 기타       | Docker, systemd, SSH, YAML, Bash Script 등  |

---

##  시스템 아키텍처

```
+----------------+      WireGuard VPN       +--------------------+
|  Local VM #1   |--------------------------|                    |
|  Local VM #2   |                          | Oracle Cloud VM     |
|  Local VM #3   |--------------------------| (Control Plane Node)|
+----------------+                          +--------------------+
     |    |    |
     v    v    v
  Kubernetes Worker Nodes (Multipass)
```

---

##  구축 절차

### 1. Multipass 기반 로컬 VM 구성
- Ubuntu 기반 VM 3대 생성
- SSH 접속 설정, 패키지 업데이트

### 2. Oracle Cloud VM 구성
- Ubuntu VM 생성
- 고정 IP 및 보안 그룹 설정 (WireGuard 포트 허용)

### 3. WireGuard VPN으로 VPC 구성
- 양쪽 피어 구성 및 터널 연결
- 라우팅 설정 및 통신 테스트

### 4. Kubernetes 클러스터 구성
- kubeadm을 통한 Master/Worker 노드 연결
- Calico CNI 설치
- 클러스터 상태 확인 (`kubectl get nodes/pods`)

### 5. Argo CD 설치 및 GitOps 배포 구성
- Argo CD 설치 및 UI 접속
- GitHub Repository와 연동
- 자동 배포 환경 구성

---

##  주요 기능

- Oracle Cloud ↔ 로컬 VM 간 VPN 기반 통신
- 멀티 노드 Kubernetes 클러스터 운영
- GitOps 방식의 자동화된 애플리케이션 배포 (Argo CD)
- 실무에 근접한 DevOps 인프라 환경 구현

---

##  프로젝트 결과

- 클라우드와 온프레미스 환경 통합에 대한 실습 경험 확보
- 쿠버네티스 클러스터 구성 능력 향상
- 배포 자동화(GitOps)의 원리와 실전 적용 가능성 학습
- 실무에서의 네트워크 설계 및 운영 고려사항 체득

---

## 🔧 향후 발전 방향

- AWS 또는 GCP 추가 연동하여 확장된 멀티 클라우드 구성
- Prometheus + Grafana를 통한 모니터링 환경 추가
- CI 파이프라인(Jenkins/GitHub Actions) 연계

---

##

---

##  프로젝트 구조 

```
multi-cloud-infra/
├── wireguard/
│   ├── wg0.conf (로컬/클라우드 설정)
├── kubernetes/
│   ├── init.sh
│   ├── kubeadm-config.yaml
│   └── calico.yaml
├── argo-cd/
│   ├── install.yaml
│   └── app-config.yaml
├── docs/
│   └── screenshots/
├── README.md
```

```
📎 이 프로젝트는 로컬 개발 환경과 클라우드를 연결하여 DevOps 환경을 구축하고자 하는 모든 분들에게 실질적인 도움이 될 수 있습니다.
```

```
