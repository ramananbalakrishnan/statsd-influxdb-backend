StatsD InfluxDB backend
-----------------------

This is a fork of the [bernd/statsd-influxdb-backend](https://github.com/bernd/stasd-influxdb-backend)

Modifications have been added to the original version, in order to support tags in InfluxDB.

Instead of using the original JSON protocol, this fork uses the [line protocol](https://docs.influxdata.com/influxdb/v0.12/write_protocols/line/) to serialize the data before sending the data via [POST /write](https://docs.influxdata.com/influxdb/v0.12/guides/writing_data/#writing-data-using-the-http-api).

This backend has been tested with InfluxDB version v0.12.2

## Configuration required in StatsD config file

In order to prevent StatsD from parsing the input and instead pass that role to this backend, make sure to add the following line to your `config.js`

```js
keyNameSanitize: false
```

## Activation

Add the `statsd-influxdb-backend` to the list of StatsD backends in the config file and restart the StatsD process.

```js
{
  backends: ['./backends/graphite', 'statsd-influxdb-backend']
}
```
