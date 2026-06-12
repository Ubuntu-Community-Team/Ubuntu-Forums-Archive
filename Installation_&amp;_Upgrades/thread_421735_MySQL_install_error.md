---
title: "MySQL install error"
date: 2007-04-24
forum: Installation &amp; Upgrades
---

### Post by hugov on 2007-04-24
HI,

I am having trouble installing mysql-server-5.0 from Synaptic Package Manager, I get the error as shown in the screenshot attached. Please can someone help me with this.

Thanks

---

### Post by ac7ss on 2007-04-24
What are the results of a ```
df
``` It sounds like you are out of space / quota in that partition.

---

### Post by hugov on 2007-04-24
I am sorry I am fairly new to linux, below is the results of df

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda7             19678772   2645080  16034052  15% /
varrun                  514056       124    513932   1% /var/run
varlock                 514056         0    514056   0% /var/lock
procbususb              514056       116    513940   1% /proc/bus/usb
udev                    514056       116    513940   1% /dev
devshm                  514056         0    514056   0% /dev/shm
lrm                     514056     38972    475084   8% /lib/modules/2.6.20-15-generic/volatile
/dev/hda1             40957684  34952180   6005504  86% /media/hda1
/dev/hda5             55769612  29183692  26585920  53% /media/hda5

---

### Post by ac7ss on 2007-04-24
according to this, you have 15 Gigs free on the primary drive...

(More than I have on the root partition.)

The only other obvious thing that I can think of is running out of quota, but that is not likely to be invoked on your machine. 

The downloadable package (Including dependencies) is rather large...

Nearly 100 megs. 

I am installing it now to see how big it installs to.

---

### Post by ac7ss on 2007-04-24
lessee, 

2551796 to 
2696984

(carry the 2...)
145188 k

140 megs.

Ok, now it is installed, what do I do with it?

---

### Post by hugov on 2007-04-25
I am using a default install from the disc, I did not set any quotas or anything. Does Ubunutu automatically set these quotas? How do I get rid of it?

---

### Post by ac7ss on 2007-04-25
they are not usually invoked... I don't know what else to say.

---

### Post by sunman6 on 2007-04-25
hugov,

open a terminal and type

sudo apt-get install mysql-server

let me know how you get on

sm

---

### Post by hugov on 2007-04-25
no, go...the terminal spits out the following:

sudo apt-get install mysql-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgems-ruby1.8 rake libredcloth-ruby1.8 libpgsql-ruby1.8 liberb-ruby libpq4
  libopenssl-ruby1.8
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  mysql-server-5.0
Suggested packages:
  tinyca
Recommended packages:
  mailx
The following NEW packages will be installed:
  mysql-server mysql-server-5.0
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 47.5kB/26.6MB of archives.
After unpacking 72.6MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty/main mysql-server 5.0.38-0ubuntu1 [47.5kB]
Fetched 47.5kB in 5s (8981B/s)       
Preconfiguring packages ...
(Reading database ... 101727 files and directories currently installed.)
Unpacking mysql-server-5.0 (from .../mysql-server-5.0_5.0.38-0ubuntu1_amd64.deb) ...
/var/lib/dpkg/tmp.ci/preinst: line 133: /usr/bin/tail: cannot execute binary file
ERROR: There's not enough space in /var/lib/mysql/
dpkg: error processing /var/cache/apt/archives/mysql-server-5.0_5.0.38-0ubuntu1_amd64.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Selecting previously deselected package mysql-server.
Unpacking mysql-server (from .../mysql-server_5.0.38-0ubuntu1_all.deb) ...
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-server-5.0_5.0.38-0ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

I hope this helps, and thank you all for trying to help, hope there will be a sollution to my problem.

---

### Post by sunman6 on 2007-04-25
i see that you are running an amd64 processor

this might be related to it somehow

did you try searching google for this issue?

sm

---

### Post by ac7ss on 2007-04-26
I installed on an amd 64 dual core, no troubles.

This seems to be a disk space/quota problem.

type "quota" and post the result.

---

