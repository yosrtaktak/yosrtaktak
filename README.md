<!-- ===================== HERO ===================== -->

<div align="center">

<img width="100%" src="https://capsule-render.vercel.app/api?type=waving&height=230&color=0:0F172A,50:164E63,100:06B6D4&text=Yosr%20Taktak&fontSize=56&fontColor=FFFFFF&fontAlignY=38&desc=Cloud%20%7C%20DevOps%20%7C%20SRE%20%7C%20Observability&descSize=17&descAlignY=59&animation=fadeIn" alt="Yosr Taktak profile banner"/>

<a href="https://git.io/typing-svg">
  <img src="https://readme-typing-svg.demolab.com?font=JetBrains+Mono&weight=500&size=18&duration=3000&pause=900&color=22D3EE&center=true&vCenter=true&width=700&lines=Building+reliable+cloud-native+systems;Kubernetes+%7C+GitOps+%7C+CI%2FCD;SLOs+%7C+Observability+%7C+Chaos+Engineering;Seeking+a+Cloud+%2F+DevOps+%2F+SRE+internship+%C2%B7+Feb%E2%80%93Apr+2027" alt="Animated introduction"/>
</a>

<br/>

<img src="https://img.shields.io/badge/Open%20to-Cloud%20%2F%20DevOps%20%2F%20SRE%20internship-22C55E?style=for-the-badge" alt="Open to internship"/>

<br/>

<a href="https://github.com/yosrtaktak/yosrtaktak/blob/main/assets/CV_Yosr_Taktak_EN.pdf">
  <img src="https://img.shields.io/badge/Resume-Download%20CV-0891B2?style=for-the-badge&logo=readdotcv&logoColor=white" alt="Download CV"/>
</a>
<a href="https://www.linkedin.com/in/yosrtaktak">
  <img src="https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"/>
</a>
<a href="mailto:yosrtaktak6@gmail.com">
  <img src="https://img.shields.io/badge/Email-Contact-EA4335?style=for-the-badge&logo=gmail&logoColor=white" alt="Email"/>
</a>

<img src="https://komarev.com/ghpvc/?username=yosrtaktak&style=flat-square&color=0891B2&label=PROFILE+VIEWS" alt="Profile views"/>

</div>

---

## `01` · About Me

```yaml
name: Yosr Taktak
role: Software Engineering Student (final year, graduating June 2027)
focus: [Cloud, DevOps, SRE, Observability]
seeking: 6-month Cloud / DevOps / SRE internship (Feb-Apr 2027)
relocation: open to relocation in Europe
latest_work: Reliability platform on K3s (SLOs, chaos engineering, GitOps, on-call automation)
location: Sfax, Tunisia
languages: Arabic (native), French (C1), English (B2)
```

I am a final-year software engineering student at the **International Institute of Technology (IIT), Sfax**. During my DevOps/SRE internship at **BePrimeTech**, I designed and validated, through chaos experiments, a full **detect → diagnose → remediate** reliability loop on Kubernetes.

I am now looking to deepen this into production-grade Cloud engineering experience within an experienced platform or infrastructure team.

---

## `02` · Technology Stack

<div align="center">
  <img width="100%" src="assets/stack.svg" alt="Technology stack: Linux, Docker, Kubernetes, K3s, Istio, Helm, Terraform, Argo CD, Prometheus, Grafana, Loki, Tempo, OpenTelemetry, Kiali, LitmusChaos and more"/>
  <br/><br/>
  <img src="https://img.shields.io/badge/AWS-Cloud%20Practitioner%20Essentials%20(course%20completed)-FF9900?style=flat-square&logo=amazonwebservices&logoColor=white" alt="Currently learning AWS"/>
</div>

---

## `03` · Reliability Platform · SRE in Action

> **DevOps & SRE Internship — BePrimeTech (Jun – Aug 2026)**: production-readiness and reliability platform for an 11-microservice e-commerce application on K3s.

<div align="center">
  <img width="100%" src="assets/key-results.svg" alt="Key results: 11 microservices, 5 SLOs, 16 alerts, 8 chaos experiments, MTTA 3 min 17 s, 6 Argo CD applications"/>
</div>

### 🔁 Delivery & observability pipeline

<div align="center">
  <img width="100%" src="assets/pipeline.svg" alt="Pipeline: Commit, CI, Argo CD, K3s, Prometheus, Grafana"/>
</div>

### 🏗️ Architecture

```mermaid
flowchart LR
    DEV([Developer]) -->|git push| GH[GitHub]
    GH --> CI[GitHub Actions<br/>Trivy · CodeQL · Gitleaks]
    TF[Terraform] -->|provisions| K3S

    subgraph K3S[K3s cluster · Istio Ambient · strict mTLS]
        direction TB
        APP[11 microservices]
        OBS[Prometheus · Loki · Tempo<br/>OpenTelemetry · Kiali]
        AM[Alertmanager]
        APP -->|metrics · logs · traces| OBS
        OBS --> AM
    end

    GH -->|manifests| ARGO[Argo CD<br/>6 applications · selfHeal]
    ARGO -->|sync| K3S
    OBS --> GRAF[Grafana<br/>5 dashboards as code]

    LITMUS{{LitmusChaos<br/>Argo Workflows}} -.->|fault injection| APP

    AM --> ONCALL[GoAlert · ntfy · Slack]
    AM --> HOLMES[HolmesGPT · Gemini<br/>Qdrant RAG · read-only]
    HOLMES -.->|proposed fix| PR[Human-reviewed PR]
    PR --> GH

    classDef main fill:#0F172A,stroke:#22D3EE,color:#E2E8F0;
    classDef chaos fill:#1E1B2E,stroke:#F43F5E,color:#E2E8F0;
    classDef ai fill:#1E1B2E,stroke:#A78BFA,color:#E2E8F0;
    class GH,CI,TF,APP,OBS,AM,ARGO,GRAF,ONCALL,PR main;
    class LITMUS chaos;
    class HOLMES ai;
```

### 💥 Chaos-validated reliability loop

<div align="center">
  <img width="100%" src="assets/reliability-loop.svg" alt="Reliability loop: inject, detect, diagnose, remediate, re-test"/>
</div>

### 🎯 SLO-based alerting

- **5 SLOs (99% – 99.95%)** defined on user-centric SLIs, measured at the mesh L7 layer
- **Multi-burn-rate alerting** following the Google SRE Workbook: 16 alerts, 8 inhibition rules, Slack routing by severity
- **Incident management:** GoAlert, ntfy, Slack war room with ChatOps, incident database
- **Hardening:** default-deny authorization policies, PodDisruptionBudgets, tuned resource limits, observability stack packaged as a single Helm chart

---

## `04` · Experience & Projects

| Period | Role | What I built |
|---|---|---|
| Jun – Aug 2026 | **DevOps & SRE Intern** · BePrimeTech | Reliability platform on K3s: SLO alerting, chaos engineering, GitOps, on-call automation |
| Feb – Jun 2025 | **Full-Stack Developer** · Collary platform | Angular 17 / Spring Boot / MySQL features for recruitment agencies and healthcare facilities |
| Feb – May 2024 | **Full-Stack Developer Intern** · IT SERV | Spring Boot microservices (Eureka, API Gateway, Config Server) for a task and timesheet platform |
| Jul – Aug 2023 | **Network Monitoring Intern** · New Engineering IT | Zabbix monitoring of Windows, Linux and web servers via agents and SNMP |

<table>
<tr>
<td width="50%" valign="top">

### 🛒 Retail ERP

Stock batch logic, audited stock movements, scheduled alerting with Firebase push, JWT roles, POS and analytics UI.

`Next.js 14` `TypeScript` `Prisma` `PostgreSQL`

</td>
<td width="50%" valign="top">

### 📈 Decision-Support Platform

Team project: automated data pipeline, analytics dashboards, sales forecasting and a local-LLM assistant.

`SQL Server` `SSIS` `SSAS` `React` `FastAPI` `Ollama`

</td>
</tr>
</table>

<div align="center">

<a href="https://github.com/yosrtaktak?tab=repositories">
  <img src="https://img.shields.io/badge/Explore-My%20Repositories-0F172A?style=for-the-badge&logo=github&logoColor=white" alt="Explore repositories"/>
</a>

</div>

---

## `05` · Contribution Graph

<div align="center">
  <img width="100%" src="profile-3d-contrib/profile-night-rainbow.svg" alt="3D contribution graph of yosrtaktak"/>
</div>

---

<div align="center">

### Build · Automate · Observe · Improve

<img width="100%" src="https://capsule-render.vercel.app/api?type=waving&height=110&section=footer&color=0:0F172A,50:164E63,100:06B6D4" alt="Decorative footer"/>

</div>
