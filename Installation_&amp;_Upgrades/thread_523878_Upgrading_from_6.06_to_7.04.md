---
title: "Upgrading from 6.06 to 7.04"
date: 2007-08-12
forum: Installation &amp; Upgrades
---

### Post by cmnorton on 2007-08-12
I received a live DVD when I purchased Ubuntu unleased. What is the official method for upgrading? I tried

# gksu "update-manager -c"

and got this warning.

(gksu:8246): Gtk-WARNING **: cannot open display:

What is the preferred method?

Thanks.

---

### Post by Bagster on 2007-08-12
I think sudo apt-get dist-upgrade should do the job

---

### Post by logos34 on 2007-08-12
you can only upgrade one release at a time, so it'll be a two-stage process- dapper-->edgy-->fesity

---

### Post by wolfen69 on 2007-08-12
if at all possible, you should get the 7.04 cd and do a clean install. you are less likely to have problems.

---

### Post by cmnorton on 2007-08-16
> **logos34 said:**
> you can only upgrade one release at a time, so it'll be a two-stage process- dapper-->edgy-->fesity

Where is the download location for edgy?

---

### Post by Seisen on 2007-08-16
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

### Post by DantePasquale on 2007-08-24
Hi, how is your upgrade going? I was going to try this upgrade in the next couple of weeks (time permitting). 

I really don't want to do a fresh install as I'm running ispconfig, mysql, postgress, jinzora, lamp, etc ... and don't want to go about configuring as I need the services especially for e-mail.

---

### Post by cmnorton on 2007-08-25
> **DantePasquale said:**
> Hi, how is your upgrade going? I was going to try this upgrade in the next couple of weeks (time permitting). 

I really don't want to do a fresh install as I'm running ispconfig, mysql, postgress, jinzora, lamp, etc ... and don't want to go about configuring as I need the services especially for e-mail.
The upgrade is on hold. I've been challenged by other things like getting a vpn connection working. In the end, I'll probably back up my important data and do a fresh install, although it might be interesting to perform a multi-stage installation. I've learned a lot by working with pptpconfig.

---

### Post by DantePasquale on 2007-10-21
HI, I tried using apt-get and it won't upgrade anything. What are the alternatives?

dante@inferno:~$ sudo apt-get -s dist-upgrade
Password:
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

