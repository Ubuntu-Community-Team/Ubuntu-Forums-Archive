---
title: "Cannot install new packages"
date: 2012-05-12
forum: Installation &amp; Upgrades
---

### Post by JackWM on 2012-05-12
I'm running Ubuntu 11.10, on a System 76 computer.

I've been having issues for the past few months, where I'm unable to install any new packages using synaptic:

```
~ sudo apt-get install abe
```
...
```
dpkg: error: read error in `/var/lib/dpkg/triggers//File': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

I get similar errors with the following:

```
~ sudo dpkg --configure -a
[sudo] password for jack: 
dpkg: error: read error in `/var/lib/dpkg/triggers//File': Input/output error

```

Using update manager returns the same errors.

Thanks in advance.

---

### Post by JackWM on 2012-05-12
Following things I have tried:

```
sudo apt-get autoclean
sudo apt-get clean 
sudo apt-get update
sudo apt-get upgrade
```
No success.

---

### Post by woxuxow on 2012-05-12
Try these

sudo apt-get --purge autoremove
sudo apt-get update
sudo apt-get upgrade

---

### Post by JackWM on 2012-05-12
> **MustafaJF said:**
> Try these

sudo apt-get --purge autoremove
sudo apt-get update
sudo apt-get upgrade

```

~ sudo apt-get --purge autoremove 
[sudo] password for jack: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 1599 not upgraded.

``````

Fetched 486 MB in 37min 40s (215 kB/s)                                         
Extracting templates from packages: 100%
Preconfiguring packages ...
dpkg: error: read error in `/var/lib/dpkg/triggers//File': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)

```Same error as I was getting before.

Thanks for your help, this has been troubling me for the past month or so.
Do you have any more ideas?

---

### Post by JackWM on 2012-05-12
I've also tried:

```

~ sudo apt-get -f install
~ sudo apt-get update
~ sudo apt-get upgrade

```

Which gives the usual error:

```

dpkg: error: read error in `/var/lib/dpkg/triggers//File': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

---

