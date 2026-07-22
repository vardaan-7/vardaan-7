<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0F2027,50:203A43,100:2C5364&height=220&section=header&text=Vardaan&fontSize=70&fontColor=ffffff&fontAlignY=35&desc=Backend%20%26%20AI%20Engineer%20%7C%20Distributed%20Systems%20%7C%20FinTech%20Enthusiast&descAlignY=58&descSize=18&animation=fadeIn" width="100%"/>

<br/>

<a href="https://www.linkedin.com/in/vardaan-shukla-b63b54264/">
  <img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white"/>
</a>
<a href="mailto:vardaan.shukla7@gmail.com">
  <img src="https://img.shields.io/badge/Gmail-D14836?style=for-the-badge&logo=gmail&logoColor=white"/>
</a>
<a href="https://leetcode.com/u/Vardaan28/">
  <img src="https://img.shields.io/badge/LeetCode-FFA116?style=for-the-badge&logo=leetcode&logoColor=black"/>
</a>
<a href="https://github.com/vardaan-7">
  <img src="https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white"/>
</a>

<br/><br/>

![Profile Views](https://komarev.com/ghpvc/?username=vardaan-7&color=2C5364&style=for-the-badge&label=PROFILE+VIEWS)
![Status](https://img.shields.io/badge/STATUS-OPEN%20TO%20WORK-brightgreen?style=for-the-badge)

<br/>

![Backend](https://img.shields.io/badge/Backend%20Engineering-2C5364?style=flat-square)
![AI](https://img.shields.io/badge/AI%20Engineering-7B2CBF?style=flat-square)
![FinTech](https://img.shields.io/badge/FinTech-0E7C61?style=flat-square)

</div>

<br/>

## `01` About Me

I build systems that survive contact with production — not notebooks that die in a Jupyter cell. My work sits at the intersection of **backend engineering and AI/ML**: I care equally about designing the model/pipeline *and* the infrastructure that actually ships it — REST APIs, caching layers, auth, containerized services, and persistent storage. I'm not choosing a lane between "backend" and "AI engineer" — I want to be the person who can do both, end to end.

```txt
class Vardaan(BackendEngineer, AIEngineer):
    def __init__(self):
        self.degree      = "B.Tech CSE (AI/ML), VIT Bhopal University"
        self.focus       = ["API Design", "Distributed Systems", "ML/AI Systems", "DB Scaling"]
        self.interests    = ["FinTech", "Recommendation Systems", "Vector Search"]
        self.philosophy   = "If it can't be deployed, it isn't finished."
        self.status       = "Actively seeking Backend / AI Engineering internships and roles"

    def currently_building(self):
        return "Artist Collaboration Engine — a location-aware discovery " \
               "platform for independent musicians, powered by vector search"
```

Most of my projects are deliberately built as **simulations of real-world production domains** — marketplaces, delivery logistics, fintech dashboards, and computer-vision pipelines — because the goal isn't "does it run," it's "could this survive a code review from a senior engineer." I'm especially drawn to **fintech** — the combination of strict correctness requirements, real-time data, and systems that have to be both fast *and* trustworthy is exactly the kind of hard problem I want to work on.

<br/>

## `02` Featured Projects

<table width="100%">
<tr>
<td width="100%">

### 🎵 Artist Collaboration Engine <sub><i>(flagship project)</i></sub>

**A location-aware discovery and collaboration platform for independent artists in the Indian music scene**, designed around a real production data stack rather than a single monolithic service.

**Engineering highlights**
- 🔎 Semantic, location-aware artist matching using **vector similarity search** (Qdrant) instead of naive keyword filtering
- ⚡ **Redis** caching layer in front of hot read paths to cut redundant PostgreSQL/Qdrant round-trips
- 🗄️ Clean separation of concerns — relational metadata in **PostgreSQL**, unstructured media in **MinIO** (S3-compatible object storage), embeddings in **Qdrant**
- 🔐 **JWT-based auth** for stateless, horizontally-scalable session handling
- 🐳 Fully containerized, multi-service local dev environment via **Docker Compose**

<p>
<img src="https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white"/>
<img src="https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white"/>
<img src="https://img.shields.io/badge/Redis-DC382D?style=flat-square&logo=redis&logoColor=white"/>
<img src="https://img.shields.io/badge/Qdrant-Vector%20DB-DD2222?style=flat-square"/>
<img src="https://img.shields.io/badge/MinIO-C72E49?style=flat-square&logo=minio&logoColor=white"/>
<img src="https://img.shields.io/badge/Docker%20Compose-2496ED?style=flat-square&logo=docker&logoColor=white"/>
<img src="https://img.shields.io/badge/JWT-Auth-black?style=flat-square&logo=jsonwebtokens"/>
</p>

<details>
<summary><b>📐 View System Architecture Diagram</b></summary>
<br/>

```mermaid
flowchart LR
    subgraph Client["🖥️ Client Layer"]
        A[Web / Mobile Client]
    end

    subgraph API["⚙️ Application Layer"]
        B["FastAPI<br/>(Async REST API)"]
        C["JWT Auth<br/>Middleware"]
    end

    subgraph Cache["⚡ Caching Layer"]
        D[("Redis<br/>Hot Read Cache")]
    end

    subgraph Data["🗄️ Persistence Layer"]
        E[("PostgreSQL<br/>Relational Metadata")]
        F[("Qdrant<br/>Vector Embeddings")]
        G[("MinIO<br/>Media / Object Storage")]
    end

    A -->|HTTPS Request| B
    B --> C
    C -->|Authenticated| B
    B -->|Cache Lookup| D
    D -->|Cache Hit| B
    D -.->|Cache Miss| E
    B -->|Structured Queries| E
    B -->|Similarity Search| F
    B -->|Upload / Fetch Media| G
    E -->|Write-through| D

    style A fill:#2C5364,color:#fff
    style B fill:#009688,color:#fff
    style C fill:#0f2027,color:#fff
    style D fill:#DC382D,color:#fff
    style E fill:#4169E1,color:#fff
    style F fill:#DD2222,color:#fff
    style G fill:#C72E49,color:#fff
```

**Request flow:** client → FastAPI → JWT validation → Redis cache check → on miss, fan-out to PostgreSQL (metadata) and Qdrant (vector similarity) → MinIO for media assets → response, with write-through cache population to keep subsequent reads fast.

</details>

📎 [`github.com/vardaan-7/Artist-collab`](https://github.com/vardaan-7/Artist-collab)

</td>
</tr>
</table>

<br/>

<table width="100%">
<tr>
<td width="50%" valign="top">

### 🍽️ ByteDine
Backend-focused food delivery system modeling restaurants, users, delivery agents, and the full order lifecycle through clean **OOP domain design**.

**Focus:** entity modeling, state transitions, order-matching logic

<img src="https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white"/>
<img src="https://img.shields.io/badge/OOP-Design-informational?style=flat-square"/>

📎 [`github.com/vardaan-7/ByteDine`](https://github.com/vardaan-7/ByteDine)

</td>
<td width="50%" valign="top">

### 📈 MarketLens <sub><i>(fintech)</i></sub>
Full-stack fintech application for stock analysis — technical indicators, backtesting, and risk-aware trend prediction across a MERN + Python pipeline.

**Focus:** data pipelines, backtesting engines, full-stack integration — built out of genuine interest in financial systems, not just as a portfolio checkbox

<img src="https://img.shields.io/badge/MongoDB-47A248?style=flat-square&logo=mongodb&logoColor=white"/>
<img src="https://img.shields.io/badge/Express.js-000000?style=flat-square&logo=express&logoColor=white"/>
<img src="https://img.shields.io/badge/React-61DAFB?style=flat-square&logo=react&logoColor=black"/>
<img src="https://img.shields.io/badge/Node.js-339933?style=flat-square&logo=node.js&logoColor=white"/>
<img src="https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white"/>

📎 [`github.com/vardaan-7/MarketLens`](https://github.com/vardaan-7/MarketLens)

</td>
</tr>
<tr>
<td width="50%" valign="top">

### 🚗 Vehicle Tracking System
Computer-vision pipeline for real-time detection, tracking, and monitoring of vehicles across video streams.

**Focus:** frame-level inference pipelines, tracking algorithms

<img src="https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white"/>
<img src="https://img.shields.io/badge/OpenCV-5C3EE8?style=flat-square&logo=opencv&logoColor=white"/>
<img src="https://img.shields.io/badge/Computer%20Vision-black?style=flat-square"/>

📎 [`github.com/vardaan-7/Vehicle-tracking-project`](https://github.com/vardaan-7/Vehicle-tracking-project)

</td>
<td width="50%" valign="top">

### 🔜 More in progress
Actively hardening repo hygiene (READMEs, `.env.example`, CI/CD) across projects and shipping v1 of the Artist Collaboration Engine.

<img src="https://img.shields.io/badge/CI%2FCD-in%20progress-yellow?style=flat-square"/>
<img src="https://img.shields.io/badge/Docs-in%20progress-yellow?style=flat-square"/>

</td>
</tr>
</table>

<br/>

## `03` Dashboard

<table width="100%">
<tr>
<td width="50%" valign="top">
<img src="https://streak-stats.demolab.com?user=vardaan-7&theme=radical&hide_border=true" width="100%"/>
</td>
<td width="50%" valign="top">
<img src="https://leetcard.jacoblin.cool/Vardaan28?theme=dark&font=Baloo%202&ext=contest" width="100%"/>
</td>
</tr>
<tr>
<td width="50%" valign="top">
<img src="https://github-readme-stats.vercel.app/api/top-langs/?username=vardaan-7&layout=compact&theme=radical&hide_border=true" width="100%"/>
</td>
<td width="50%" valign="top">
<img src="https://github-readme-stats.vercel.app/api?username=vardaan-7&show_icons=true&theme=radical&hide_border=true&count_private=true" width="100%"/>
</td>
</tr>
</table>

**LeetCode contribution heatmap**

<div align="center">
<img src="https://leetcard.jacoblin.cool/Vardaan28?theme=dark&font=Baloo%202&ext=heatmap" width="100%"/>
</div>

**GitHub contribution graph**

<div align="center">
<img src="https://github-readme-activity-graph.vercel.app/graph?username=vardaan-7&theme=react-dark&hide_border=true" width="100%"/>
</div>

<details>
<summary><b>🏆 GitHub Trophies</b></summary>
<br/>
<div align="center">
<img src="https://github-profile-trophy.vercel.app/?username=vardaan-7&theme=radical&no-frame=true&row=1&column=6"/>
</div>
</details>

> ⚠️ **Why cards break:** these are all free, shared, no-auth widget services (Vercel-hosted). They occasionally rate-limit or go down — it's not your README, it's their server load. See the fix notes below the table if a card is still blank after a hard refresh.

<br/>

## `04` Technical Core Competencies

<table width="100%">
<tr><th align="left" width="30%">Domain</th><th align="left">Depth</th></tr>
<tr>
<td valign="top"><b>🗄️ Database Scaling</b></td>
<td>

PostgreSQL schema design and indexing strategy · vector embedding indexes (Qdrant HNSW) for approximate nearest-neighbor search at scale · query optimization over naive ORM defaults

</td>
</tr>
<tr>
<td valign="top"><b>⚡ Async API Architecture</b></td>
<td>

FastAPI async request pipelining · non-blocking I/O for high-concurrency endpoints · JWT-based stateless auth for horizontal scalability

</td>
</tr>
<tr>
<td valign="top"><b>🐳 Container Orchestration</b></td>
<td>

Docker and multi-service Docker Compose networks · service isolation and inter-container communication · reproducible local dev environments

</td>
</tr>
<tr>
<td valign="top"><b>🧊 Data Caching Strategy</b></td>
<td>

Redis read-through / write-through caching layers · hot-path latency reduction · cache invalidation strategy for consistency with source-of-truth stores

</td>
</tr>
<tr>
<td valign="top"><b>🤖 AI/ML Systems</b></td>
<td>

Machine learning and deep learning fundamentals · vector search and semantic similarity (Qdrant/HNSW) · recommendation system design · bridging model output to production APIs — the "last mile" most ML projects skip

</td>
</tr>
<tr>
<td valign="top"><b>💹 FinTech Systems Thinking</b></td>
<td>

Backtesting engine design · technical indicator pipelines · risk-aware prediction — drawn to fintech's combination of correctness, real-time data, and scale

</td>
</tr>
</table>

<br/>

## `05` Full Toolbox

<div align="center">

<img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white"/>
<img src="https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black"/>
<img src="https://img.shields.io/badge/SQL-4479A1?style=for-the-badge&logo=postgresql&logoColor=white"/>
<br/>
<img src="https://img.shields.io/badge/FastAPI-009688?style=for-the-badge&logo=fastapi&logoColor=white"/>
<img src="https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=node.js&logoColor=white"/>
<img src="https://img.shields.io/badge/Express-000000?style=for-the-badge&logo=express&logoColor=white"/>
<br/>
<img src="https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white"/>
<img src="https://img.shields.io/badge/Redis-DC382D?style=for-the-badge&logo=redis&logoColor=white"/>
<img src="https://img.shields.io/badge/Qdrant-DD2222?style=for-the-badge"/>
<br/>
<img src="https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white"/>
<img src="https://img.shields.io/badge/MinIO-C72E49?style=for-the-badge&logo=minio&logoColor=white"/>
<img src="https://img.shields.io/badge/JWT-black?style=for-the-badge&logo=jsonwebtokens"/>
<img src="https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white"/>

</div>

<br/>

## `06` Let's Build Something

I'm currently shipping **v1 of the Artist Collaboration Engine** and sharpening fundamentals across both system design/DB scaling and applied ML — and always up for collaborating on **distributed systems, AI-powered products, or fintech infrastructure.**

Actively looking for **backend engineering and AI engineering internships / entry-level roles** — fintech companies especially welcome. If your team is solving hard infrastructure or ML-systems problems, my inbox is open.

<div align="center">

<a href="https://www.linkedin.com/in/vardaan-shukla-b63b54264/">
  <img src="https://img.shields.io/badge/Let's%20Connect-0077B5?style=for-the-badge&logo=linkedin&logoColor=white"/>
</a>
<a href="mailto:vardaan.shukla7@gmail.com">
  <img src="https://img.shields.io/badge/Say%20Hello-D14836?style=for-the-badge&logo=gmail&logoColor=white"/>
</a>

<br/><br/>

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:2C5364,100:0F2027&height=100&section=footer"/>

</div>
