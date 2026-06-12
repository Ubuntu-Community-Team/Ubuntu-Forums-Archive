---
title: "apt-get errors after upgrade to 12.04 server"
date: 2013-04-11
forum: Installation &amp; Upgrades
---

### Post by crazyk4952 on 2013-04-11
I upgraded from Ubuntu server 11.04 to 12.04 using 
```
[COLOR=#000000][FONT=Ubuntu Mono]sudo do-release-upgrade -d[/FONT][/COLOR]
```

However, now I have the following errors with apt-get that I am unable to resolve:

[FONT=courier new]Setting up initscripts (2.88dsf-13.10ubuntu11.1) ...[/FONT]
[FONT=courier new]mkdir: cannot create directory `/dev/shm': File exists[/FONT]
[FONT=courier new]dpkg: error processing initscripts (--configure):[/FONT]
[FONT=courier new] subprocess installed post-installation script returned error exit status 1[/FONT]
[FONT=courier new]dpkg: dependency problems prevent configuration of procps:[/FONT]
[FONT=courier new] procps depends on initscripts; however:[/FONT]
[FONT=courier new]  Package initscripts is not configured yet.[/FONT]
[FONT=courier new]dpkg: error processing procps (--configure):[/FONT]
[FONT=courier new] dependency problems - leaving unconfigured[/FONT]
[FONT=courier new]dpkg: dependency problems prevent configuration of apache2.2-common:[/FONT]
[FONT=courier new] apache2.2-common depends on procps; however:[/FONT]
[FONT=courier new]  Package procps is not configured yet.[/FONT]
[FONT=courier new]dpkg: error processing apache2.2-common (--configure):[/FONT]
[FONT=courier new] dependency problems - leaving unconfigured[/FONT]
[FONT=courier new]dpkg: dependency problems prevent configuration of apache2-mpm-worker:[/FONT]
[FONT=courier new] apache2-mpm-worker depends on apache2.2-common (= 2.2.22-1ubuntu1.3); however:[/FONT]
[FONT=courier new]  Package apache2.2-common is not configured yet.[/FONT]
[FONT=courier new]dpkg: error processing apache2-mpm-worker (--configure):[/FONT]
[FONT=courier new] dependency problems - leaving unconfigured[/FONT]
[FONT=courier new]dpkg: dependency problems prevent configuration of apache2:[/FONT]
[FONT=courier new] apache2 depends on apache2-mpm-worker (= 2.2.22-1ubuntu1.3) | apache2-mpm-prefork (= 2.2.22-1ubuntu1.3) | apache2-mpm-event (= 2.2.22-1ubuntu1.3) | apache2-mNo apport report written because the error message indicates its a followup error from a previous failure.[/FONT]
[FONT=courier new]                        No apport report written because the error message indicates its a followup error from a previous failure.[/FONT]
[FONT=courier new]                                                  No apport report written because MaxReports is reached already[/FONT]
[FONT=courier new]                                No apport report written because MaxReports is reached already[/FONT]
[FONT=courier new]              No apport report written because MaxReports is reached already[/FONT]
[FONT=courier new]                                                                            pm-itk (= 2.2.22-1ubuntu1.3); however:[/FONT]
[FONT=courier new]  Package apache2-mpm-worker is not configured yet.[/FONT]
[FONT=courier new]  Package apache2-mpm-prefork is not installed.[/FONT]
[FONT=courier new]  Package apache2-mpm-event is not installed.[/FONT]
[FONT=courier new]  Package apache2-mpm-itk is not installed.[/FONT]
[FONT=courier new] apache2 depends on apache2.2-common (= 2.2.22-1ubuntu1.3); however:[/FONT]
[FONT=courier new]  Package apache2.2-common is not configured yet.[/FONT]
[FONT=courier new]dpkg: error processing apache2 (--configure):[/FONT]
[FONT=courier new] dependency problems - leaving unconfigured[/FONT]
[FONT=courier new]dpkg: dependency problems prevent configuration of openssh-server:[/FONT]
[FONT=courier new] openssh-server depends on procps; however:[/FONT]
[FONT=courier new]  Package procps is not configured yet.[/FONT]
[FONT=courier new]dpkg: error processing openssh-server (--configure):[/FONT]
[FONT=courier new] dependency problems - leaving unconfigured[/FONT]
[FONT=courier new]Setting up mysql-server (5.5.29-0ubuntu0.12.04.2) ...[/FONT]
[FONT=courier new]Errors were encountered while processing:[/FONT]
[FONT=courier new] initscripts[/FONT]
[FONT=courier new] procps[/FONT]
[FONT=courier new] apache2.2-common[/FONT]
[FONT=courier new] apache2-mpm-worker[/FONT]
[FONT=courier new] apache2[/FONT]
[FONT=courier new] openssh-server[/FONT]
[FONT=courier new]E: Sub-process /usr/bin/dpkg returned an error code (1)
[/FONT]
Any thoughts on how I can fix this?

---

### Post by ibjsb4 on 2013-04-11
Try

```
sudo dpkg --configure -a

sudo apt-get -f install
```

---

### Post by crazyk4952 on 2013-04-11
> **ibjsb4 said:**
> Try

```
sudo dpkg --configure -a

sudo apt-get -f install
```

Thanks. I tried that and unfortunately, it did not fix the problem.

---

