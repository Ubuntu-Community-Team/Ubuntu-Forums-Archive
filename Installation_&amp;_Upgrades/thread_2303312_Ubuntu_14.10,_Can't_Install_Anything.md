---
title: "Ubuntu 14.10, Can't Install Anything"
date: 2015-11-17
forum: Installation &amp; Upgrades
---

### Post by bryan57 on 2015-11-17
Hello,

I am a new Ubuntu user and am having trouble installing anything from the terminal. I have read into the error message I am getting, but I have yet to find a solution that can solve my problem. To start, here is what happens when I try to install VLC

```
bryan@REAL-GAINS:~$ sudo apt-get install vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package vlc
```

---

### Post by Vladlenin5000 on 2015-11-17
Hi and welcome.

14.10 is out of support since a long time ago -> no software repositories -> no software to install.
You should do a backup if you haven't already and install a supported version from scratch: 14.04 LTS or the current 15.10.

---

### Post by sammiev on 2015-11-17
Hi Bryan57,

LTS stands for Long Term Support and 14.04LTS will be supported into 2019.

15.10 only has about a 10 month life but maybe required for the latest drivers.

Here's the [Release end of life]("http://www.ubuntu.com/info/release-end-of-life") list.

---

### Post by Bucky Ball on 2015-11-17
> **sammiev said:**
> 15.10 only has about a 10 month life ...

Interim releases now have nine months support, so 15.10 is down to about eight. :D

Both 14.04 LTS and 15.10 are upgradeable via the net to 16.04 LTS, supported until 2021, in the second half of next year.

---

