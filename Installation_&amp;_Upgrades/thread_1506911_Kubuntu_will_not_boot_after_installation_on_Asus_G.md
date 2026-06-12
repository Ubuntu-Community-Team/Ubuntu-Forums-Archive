---
title: "Kubuntu will not boot after installation on Asus G50V"
date: 2010-06-10
forum: Installation &amp; Upgrades
---

### Post by ARam1024 on 2010-06-10
I installed Kubuntu 10.04, and everything seemed to work correctly. It asked me to restart, and I did. However, when I restarted, it went straight to Windows 7. The first time I did this, I realized that I had installed Kubuntu onto a logical partition instead of a primary one. However, installing it onto a primary partition yielded the same results. I checked in gparted live that the Kubuntu partition was in fact primary and had the boot flag.

The laptop has 2 hard drives. One is used for operating systems and 1 for data. I've made sure that Kubuntu was on the OS hard drive with Windows 7 and that that hard drive has the correct boot priority.

---

### Post by ARam1024 on 2010-06-12
Does anyone have any idea why it would be ignoring the boot flag on the Kubuntu partition and loading Windows 7 instead?

---

### Post by ARam1024 on 2010-06-17
I did manage to get Kubuntu working by installing it on the second hard drive

---

