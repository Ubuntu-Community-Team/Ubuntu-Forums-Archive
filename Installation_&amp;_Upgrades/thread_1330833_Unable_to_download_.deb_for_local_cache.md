---
title: "Unable to download .deb for local cache"
date: 2009-11-18
forum: Installation &amp; Upgrades
---

### Post by yenner on 2009-11-18
I configured synaptic to download all packages in local cache. But when i look in /var/cache/apt/archives after an installation, are not there. What is the problem. 

I am working with ubuntu 9.10.

Thank you for your time.

---

### Post by earthpigg on 2009-11-18
hello,

may i ask what you configured, and how?

what you describe is exactly how synaptic works ***by default***, so i wonder if perhaps you made a mistake and followed a how-to guide to accomplish the ***exact opposite*** of what you where actually after?

---

### Post by yenner on 2009-11-24
I know that is the default behavior of synaptic. I have worked with Debian and Ubuntu and this is first time that this happen . The problem has been with the distributions Ubuntu 9.10 and Ubuntu 9.04 . I want to create  a repo and I can not  becouse i have not the packages.

---

### Post by earthpigg on 2009-11-24
> when i look in /var/cache/apt/archives after an installation

ooook, now i get it.

if you want that directory to be full of .debs of packages ***that where included in the initial system install***, you would need to do what debian calls a 'net install'.... in ubuntu, the equivalent would be to use the mini.iso to install.

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

