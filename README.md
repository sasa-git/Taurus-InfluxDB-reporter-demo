# Taurus Influxdb reporter demo

Influxdb reporter demo

[document](https://gettaurus.org/docs/Reporting/#Influxdb-Reporter)

## Notes

run taurus

```
docker run -it --rm --entrypoint=bash -v $PWD:/var/taurus blazemeter/taurus

docker run -it --rm -v $PWD:/bzt-configs blazemeter/taurus example.yml
```


influxdb

command example

```
docker run --name=influxdb -d -p 8086:8086 -p 8083:8083 -e INFLUXDB_ADMIN_ENABLED=true influxdb:1.2

docker exec -it influxdb bash
root@1e9a8d18c95d:/# influx -precision rfc3339
```

endpoint: `http://localhost:8083/`

database: jmeter

example query

```sql
select * from taurus where "status" = 'all'

select count(*) from taurus

DROP MEASUREMENT taurus
```


grafana

```
docker run --name=grafana -d -p 3000:3000 grafana/grafana
```

influxdb_URL: `http://172.17.0.2:8086`
