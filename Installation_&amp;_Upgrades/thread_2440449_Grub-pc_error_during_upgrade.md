---
title: "Grub-pc error during upgrade"
date: 2020-04-10
forum: Installation &amp; Upgrades
---

### Post by rsteinmetz70112 on 2020-04-10
During a routinue upgrade using apt I encountered an error. 
This is 64bit 18.04 LTS and it used to work honest!

Here is the output 
#```
 apt upgrade
...
Errors were encountered while processing:
 grub-pc
E: Sub-process /usr/bin/dpkg returned an error code (1)
# apt install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up grub-pc (2.02-2ubuntu8.15) ...
dpkg: error processing package grub-pc (--configure):
 installed grub-pc package post-installation script subprocess returned error exit status 20
Errors were encountered while processing:
 grub-pc
E: Sub-process /usr/bin/dpkg returned an error code (1)
# dpkg --configure -a
Setting up grub-pc (2.02-2ubuntu8.15) ...
dpkg: error processing package grub-pc (--configure):
 installed grub-pc package post-installation script subprocess returned error exit status 20
Errors were encountered while processing:
 grub-pc
# 

```
Any idea how to clear this error.
I have tried re-installing grub-pc

Would purging grub-pc and reinstalling have a change?

Here are the results of a couble of clean-up commands

```
# apt autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up grub-pc (2.02-2ubuntu8.15) ...
dpkg: error processing package grub-pc (--configure):
 installed grub-pc package post-installation script subprocess returned error exit status 20
Errors were encountered while processing:
 grub-pc
E: Sub-process /usr/bin/dpkg returned an error code (1)
# apt autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Del apport-gtk 2.20.9-0ubuntu7.13 [9,696 B]
Del firefox 74.0+build3-0ubuntu0.18.04.1 [51.9 MB]
Del python3-problem-report 2.20.9-0ubuntu7.13 [10.5 kB]
Del linux-libc-dev 4.15.0-91.92 [1,026 kB]
Del apport 2.20.9-0ubuntu7.13 [124 kB]
Del python3-apport 2.20.9-0ubuntu7.13 [82.1 kB]
#
```

---

### Post by oldfred on 2020-04-10
May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Be sure to use Ubuntu live installer of current version & install into that using ppa. Boot-Repair ISO is older.
Make sure you boot Ubuntu live installer in same boot mode as install.

---

### Post by Impavidus on 2020-04-11
Have you done any customisations to grub?

---

### Post by rsteinmetz70112 on 2020-04-11
> **Impavidus said:**
> Have you done any customizations to grub?

No. It is as originally install. I do as little customization as I can.

---

### Post by rsteinmetz70112 on 2020-04-11
> **oldfred said:**
> May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Be sure to use Ubuntu live installer of current version & install into that using ppa. Boot-Repair ISO is older.
Make sure you boot Ubuntu live installer in same boot mode as install.

Unfortunately I'm working remotely and rebooting using alternate media is not possible, I can't get to the machine.

---

