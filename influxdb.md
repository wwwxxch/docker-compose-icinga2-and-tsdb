check service up
```bash
curl -X GET 'http://localhost:8086/health'
```

create database
```bash
curl -X POST 'http://localhost:8086/query' --data-urlencode "q=CREATE DATABASE icinga2"
curl 'http://localhost:8086/query' --data-urlencode "q=SHOW DATABASES"
```

query
```bash
curl -G 'http://localhost:8086/query?pretty=true' --data-urlencode "q=SELECT * FROM disk" --data-urlencode "db=icinga2"
curl -G 'http://localhost:8086/query?pretty=true' --data-urlencode "q=SELECT metric, value, unit FROM disk WHERE  metric = '/data' AND time > now() - 5m" --data-urlencode "db=icinga2"

# MetricsQL: disk_value{metric='/data'}
# Other MetricsQL: icinga_value{metric="avg_execution_time"}
```



