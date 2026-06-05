# microservice-docker-afl-2

Aplikasi web sederhana login dan register menggunakan Flask + PostgreSQL + Nginx, dikemas dalam Docker.

## Stack

- Python (Flask) sebagai web framework
- PostgreSQL sebagai database
- Nginx sebagai load balancer
- Docker + Docker Compose untuk orkestrasi container

## Struktur Project

```
microservice-docker-afl-2/
├── docker-compose.yml
├── nginx/
│   └── nginx.conf
└── web/
    ├── Dockerfile
    ├── requirements.txt
    ├── app.py
    └── templates/
        ├── login.html
        ├── register.html
        └── dashboard.html
```

## Cara Menjalankan

Pastikan Docker Desktop sudah berjalan, lalu jalankan perintah berikut di dalam folder project:

```bash
docker-compose up --build
```

Buka browser dan akses:

```
http://localhost:8080
```

## Fitur

- Register akun baru (username, password, confirm password)
- Login dengan akun yang sudah terdaftar
- Dashboard menampilkan username yang sedang login
- Logout

## Catatan

- Data PostgreSQL disimpan di Docker volume `pgdata` sehingga tidak hilang saat container di-restart
- Nginx mendistribusikan request ke 2 instance Flask (web1 dan web2)
- Semua service berjalan dalam satu Docker network `afl2_network`
