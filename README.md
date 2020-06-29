# Icecast exporter for Prometheus

This is a simple [Prometheus](https://prometheus.io/) exporter that scrapes stats from the [Icecast](http://icecast.org/) streaming media server. It requires the JSON API (`/status-json.xsl`)
provided by Icecast 2.4.0 or newer.

By default icecast_exporter listens on port 9146 for HTTP requests.

## Installation

### Using `go get`

```bash
go get github.com/markuslindenberg/icecast_exporter
```
### Using Docker

```
docker pull markuslindenberg/icecast_exporter
docker run --rm -p 9146:9146 markuslindenberg/icecast_exporter -icecast_scrape_uri http://icecast:8000/status-json.xsl
docker run --rm -p 9146:9146 -e ICECAST_SCRAPE_URI=http://icecast:8000/status-json.xsl markuslindenberg/icecast_exporter
```

# Running

Help on flags:
```
go run icecast_exporter --help

Usage of ./icecast_exporter:
  -icecast_scrape_uri string
    	URI on which to scrape Icecast. (default "http://localhost:8000/status-json.xsl")
  -icecast_timeout duration
    	Timeout for trying to get stats from Icecast. (default 5s)
  -log.format value
    	Set the log target and format. Example: "logger:syslog?appname=bob&local=7" or "logger:stdout?json=true" (default "logger:stderr")
  -log.level value
    	Only log messages with the given severity or above. Valid levels: [debug, info, warn, error, fatal]
  -web_listen_address string
    	Address to listen on for web interface and telemetry. (default ":9146")
  -web_telemetry_path string
    	Path under which to expose metrics. (default "/metrics")
```
