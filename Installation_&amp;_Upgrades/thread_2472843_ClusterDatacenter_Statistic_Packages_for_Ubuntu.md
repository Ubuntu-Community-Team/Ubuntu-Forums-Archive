---
title: "Cluster/Datacenter Statistic Packages for Ubuntu?"
date: 2022-03-14
forum: Installation &amp; Upgrades
---

### Post by windows7ge on 2022-03-14
I have a number of Ubuntu/Debian based network clients. Some based off diskless network boot, some hosting hypervisors.

What I'd like to do is find package software that is relatively simple to use for monitoring the resources available/in use by the cluster.

If that doesn't make sense I'm looking for something similar to what PROXMOX or VMware vCenter use to display online/offline network nodes and cumulative resources like network wide number of CPUs/RAM/Storage/etc.

I'm fine with CLI or WebUI if any packages exist for either. Every node is running Ubuntu/Ubuntu Server so I should be able to install client software to all of them and monitor their status from one location.

Thanks!

---

### Post by breakdaze on 2022-03-15
Also try hitting up the server team on IRC [https://wiki.ubuntu.com/ServerTeam/](https://wiki.ubuntu.com/ServerTeam/)

---

### Post by The Cog on 2022-03-16
It may be worth looking at Prometheus for collecting statistics, and at Grafana for serving graphs etc. from Prometheus's database. It's not too hard to set up and there are a number of ready-made reports that I think would suit you. You do need to install an "exporter" on each computer that Prometheus can query periodically.
[https://en.wikipedia.org/wiki/Prometheus_(software)](https://en.wikipedia.org/wiki/Prometheus_(software))
[https://prometheus.io/](https://prometheus.io/)
[https://grafana.com/](https://grafana.com/)
We use them where I work, and I had them running at home until my Raspberry Pi died.

---

