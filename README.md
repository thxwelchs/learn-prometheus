# Prometheus로 모니터링 하기

### mysqld_exporter에서 db 상태를 수집할 수 있게 유저 생성, 권한 할당 필요
```sql
CREATE USER 'yourdbuser'@'host' IDENTIFIED BY 'yourdbpass' WITH MAX_USER_CONNECTIONS 3;
GRANT PROCESS, REPLICATION CLIENT, SELECT ON *.* TO 'yourdbuser'@'host';
```

### 프로메테우스 docker로 실행하기
```shell
$ docker-compose up -e DATA_SOURCE={yourdbuser}:{yourdbpass}@({yourdbhost}:{yourdbport})/{yourdb}

```

### 해볼 것 
- Grafana 연동
- MySQL 상태 모니터링 (Grafana)
- Server 상태 모니터링 (Grafana)
- 뭐 할지 생각 아마 k8s에 적용