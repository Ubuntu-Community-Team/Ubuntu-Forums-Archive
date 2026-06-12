---
title: "Apache solr Installation Issues"
date: 2024-10-26
forum: Installation &amp; Upgrades
---

### Post by SAH62 on 2024-10-26
I just installed Ubuntu 24.04.1 LTS on a Dell 5820 workstation. The OS seems to be working just fine.

Now I'm trying to get Apache solr installed and working. This is the version of Java I'm running:

```
$ java --version
openjdk 21.0.4 2024-07-16
OpenJDK Runtime Environment (build 21.0.4+7-Ubuntu-1ubuntu224.04)
OpenJDK 64-Bit Server VM (build 21.0.4+7-Ubuntu-1ubuntu224.04, mixed mode, sharing)

```

I installed solr version 9.7.0. The installation went fine. I can start the solr service. Here's the status after it starts:

```
$ sudo systemctl status solr
&#9679; solr.service - LSB: Controls Apache Solr as a Service
     Loaded: loaded (/etc/init.d/solr; generated)
     Active: active (exited) since Sat 2024-10-26 18:27:30 EDT; 14min ago
       Docs: man:systemd-sysv-generator(8)
    Process: 16940 ExecStart=/etc/init.d/solr start (code=exited, status=0/SUCCESS)
        CPU: 24ms


Oct 26 18:27:28 myhost systemd[1]: Starting solr.service - LSB: Controls Apache Solr as a Service...
Oct 26 18:27:28 myhost su[16944]: (to solr) root on none
Oct 26 18:27:28 myhost su[16944]: pam_unix(su-l:session): session opened for user solr(uid=106) by (uid=0)
Oct 26 18:27:30 myhost solr[17008]: Started Solr server on port 8983 (pid=17001). Happy searching!
Oct 26 18:27:30 myhost systemd[1]: Started solr.service - LSB: Controls Apache Solr as a Service.

```

Note "Active: active (exited)". I've added a firewall rule to open port tcp/8983; here's the output from iptables:

```
ACCEPT     6    --  127.0.0.1            0.0.0.0/0            tcp dpt:8983
ACCEPT     6    --  192.168.1.46         0.0.0.0/0            tcp dpt:8983
```

Attempts to connect to the server using a browser with URL [http://192.168.1.250:8983/](http://192.168.1.250:8983/) time out. The connection attempt is being refused according to iptables.

```
2024-10-26T18:53:51.741381-04:00 localhost kernel: iptables denied: IN=eno1 OUT= MAC=54:bf:64:94:de:a8:d8:bb:c1:94:72:25:08:00 SRC=192.168.1.46 DST=192.168.1.250 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=20939 DF PROTO=TCP SPT=61547 DPT=8983 WINDOW=64240 RES=0x00 SYN URGP=0

```

Can someone please help me understand what's going on here? Why is the service not in an active (running) state? Why is iptables blocking the connection request when the port is open?

---

