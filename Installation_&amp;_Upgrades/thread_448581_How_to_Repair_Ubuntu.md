---
title: "How to Repair Ubuntu"
date: 2007-05-19
forum: Installation &amp; Upgrades
---

### Post by BRUNOALVISIO on 2007-05-19
Hi,

During the last few days , ubnutu started showing some errors while I was running it. I would like to repair all this erros by restallling it but I don't want to lose all the programs  that I have laready installed.

What  should I do?

Thnks 

Bruno

---

### Post by taurus on 2007-05-19
If you want to repair it, you need to specify what errors do you get or else nobody would know what you are talking about?

---

### Post by kissLA on 2007-05-23
Hello, i'm using ubuntu 6.06LTS on an old lifebook von fujitsu siemens (P3). today when i tried to install the 3d accerlation, the system can't start in x but in command-line after rebooting. some1 help me repair this please! i think the xorg conf. is overwritten but dun know how to access.

---

### Post by taurus on 2007-05-23
Try

```
sudo dpkg-reconfigure xserver-xorg
```
What video card do you have on that laptop?

---

### Post by kissLA on 2007-05-23
Thanks for ur answer. Its said that xserver-org is not installed. i dun understand. i did use it before it corrupts

i'm not very sure about this but the grafic card is ATI something

---

