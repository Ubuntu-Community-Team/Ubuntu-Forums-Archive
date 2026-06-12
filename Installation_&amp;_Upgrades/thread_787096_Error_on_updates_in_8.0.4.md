---
title: "Error on updates in 8.0.4"
date: 2008-05-08
forum: Installation &amp; Upgrades
---

### Post by phil888 on 2008-05-08
I am getting the following error message when trying to install updates or add packages through synaptic:

"E: /var/cache/apt/archives/mount_2.13.1-5ubuntu2_i386.deb: failed in buffer_read(fd)"

The updates and installs all fail. 

Any suggestions.

---

### Post by Partyboi2 on 2008-05-08
What happens when you run in a terminal (Applications>Accessories>Terminal)
```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```or
```
sudo apt-get -f install
```another thing to check is how much space you have left on your drive maybe you are running out of room.
```
df -h
```

---

### Post by phil888 on 2008-05-09
> **Partyboi2 said:**
> What happens when you run in a terminal (Applications>Accessories>Terminal)
```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```or
```
sudo apt-get -f install
```another thing to check is how much space you have left on your drive maybe you are running out of room.
```
df -h
```

Thanks but it did not solve problem.

sudo apt-get -f install

returned the following

"~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 63 not upgraded."

sudo apt-get clean was fine
sudo apt-get update showed 63 packages available
sudo apt-get upgrade proceeded with downloading the packages which went fine then when the download was finished I received the following:

"Fetched 44.1MB in 8min10s (89.9kB/s)                                           
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/mount_2.13.1-5ubuntu2_i386.deb (--unpack):
 failed in buffer_read(fd): files list for package `xsltproc': Input/output error
Errors were encountered while processing:
 /var/cache/apt/archives/mount_2.13.1-5ubuntu2_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)" 

There is 5.1 gig of disk space available.

I get a similar error when trying to add software with synaptic.

---

### Post by hermes0710 on 2008-05-09
Try emptying the folder /var/cache/apt/archives since it has broken packages dowloaded and retry

---

### Post by phil888 on 2008-05-12
> **hermes0710 said:**
> Try emptying the folder /var/cache/apt/archives since it has broken packages dowloaded and retry

Emptying directory did not work either. Thanks for replies. I reinstalled and now all seems to be working fine.

---

