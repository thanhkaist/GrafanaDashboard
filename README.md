#  PROMETHEUS + GRAFANA DASHBOARD
## Overview
### COMPONENTS:

- Prometheus: the master server to Pull data from all nodes that we want to monitor
- Grafana: Get data from Prometheus and visualize them to the Dashboard 
- Node exporter: CPU + system data export slave
- DCGM exporter: GPU data export slave 

### HOW TO SETUP:

- We need to install Prometheus and Grafana on only one server (i.e monitor server)
- On each server we want to monitor (i.e node server), we need to install Node exporter and DCGM exporter
- Update config for Prometheus to Pull data from nodes.
- Open Grafana web and set up the dashboard for viewing.

## Bring up services
- On monitor server 
```bash
docker compose up -d
```
- On each node server 

```bash
cd dcgmexport 
docker compose up -d
cd ../nodeexporter
docker compose up -d
```

## Access web apps

- prometheus: Open the browser at ```http:localhost:9090``` 
- grafana: Open the browser at ```http:localhost:3000``` 

    - User: admin
    - Pass: admin


## Setup datasource and Dashboard in Grafana

Step 1: Configure Grafana for Prometheus Data Source:
- Log in to Grafana using the default credentials.
- Navigate "Connections/Data Sources"
- Click on “Add data source.”
- Choose “Prometheus” from the list.
- Set the URL to http://143.248.158.41:9090.
- Click “Save & Test” to verify the connection.


Step 2: Importing Dashboard using Grafana Web UI:
- On the left sidebar, Navigate to Dashboards, Click Create Dashboard
- Select “Import dashboard” to access the Import Dashboard page.
- Import GPU-management-Dashboard.json