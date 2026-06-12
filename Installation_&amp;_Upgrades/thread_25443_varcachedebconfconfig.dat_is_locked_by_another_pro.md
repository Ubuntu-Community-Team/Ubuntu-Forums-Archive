---
title: "/var/cache/debconf/config.dat is locked by another proces"
date: 2005-04-10
forum: Installation &amp; Upgrades
---

### Post by vartere on 2005-04-10
Hi,
when i use apt-get to install some programs, e.g. "samba" i recive the follow output:

```
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  samba-doc
The following NEW packages will be installed:
  samba
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 2356kB of archives.
After unpacking 6099kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com hoary/main samba 3.0.10-1ubuntu3 [2356kB]
Fetched 2356kB in 4s (474kB/s)
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process
Selezionato il pacchetto samba, che non lo era.
(Lettura del database ... 73565 file e directory attualmente installati.)
Spacchetto samba (da .../samba_3.0.10-1ubuntu3_i386.deb) ...
Configuro samba (3.0.10-1ubuntu3) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process
dpkg: errore processando samba (--configure):
 il sottoprocesso post-installation script ha restituito un codice di errore 1
Sono occorsi degli errori processando:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)
``` 


/var/cache/debconf/config.dat is locked by another process , but what is this process?
I search in System monitor between all processes, but i can't found config.dat in arguments.
Help me.
Thanks

vartere

---

### Post by localzuk on 2005-04-10
Take a look at lsof to find the process using the file. eg.

lsof /var/cache/debconf/config.dat

---

### Post by vartere on 2005-04-10
i'm so confuse

there are many processes that use this file
look that:

```
root@motousate:/home/vartere # lsof /var/cache/debconf/config.dat
root@motousate:/home/vartere # lsof /var/cache/debconf/config.dat
COMMAND     PID USER   FD   TYPE DEVICE  SIZE    NODE NAME
debconf-c 12170 root    4rW  REG    8,2 66547 2240840 /var/cache/debconf/config.dat
root@motousate:/home/vartere # lsof /var/cache/debconf/config.dat
root@motousate:/home/vartere # lsof /var/cache/debconf/config.dat
COMMAND     PID USER   FD   TYPE DEVICE  SIZE    NODE NAME
debconf-c 12185 root    4rW  REG    8,2 66547 2240840 /var/cache/debconf/config.dat
root@motousate:/home/vartere # lsof /var/cache/debconf/config.dat
^[[ACOMMAND     PID USER   FD   TYPE DEVICE  SIZE    NODE NAME
debconf-c 12203 root    5rW  REG    8,2 66547 2241469 /var/cache/debconf/config.dat
root@motousate:/home/vartere # lsof /var/cache/debconf/config.dat
COMMAND     PID USER   FD   TYPE DEVICE  SIZE    NODE NAME
debconf-c 12203 root    5rW  REG    8,2 66547 2241469 /var/cache/debconf/config.dat
root@motousate:/home/vartere #
``` 

it's normal?
i can't install with apt-get the samba, but i can other programs like xmms.

---

### Post by vartere on 2005-04-10
i don't known, but i re-installed the system again and the problem disappered.

thanks a lot

---

### Post by sml on 2005-09-05
To find the process using the file try:
#fuser -v /var/cahce/debconf/config.dat

I have an app called 'frontend' using config.dat and now my apt-get is broken!

---

