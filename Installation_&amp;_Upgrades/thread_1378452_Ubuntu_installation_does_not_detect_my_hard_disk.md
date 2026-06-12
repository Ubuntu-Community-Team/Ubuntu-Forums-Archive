---
title: "Ubuntu installation does not detect my hard disk"
date: 2010-01-11
forum: Installation &amp; Upgrades
---

### Post by Aditya Kulkarni on 2010-01-11
I have been trying to install Ubuntu from the live CD but during the 4th out of 7th step comes it does not detect my hard disk.

Nothing is shown in the forth step.

Please help me

---

### Post by SecretCode on 2010-01-11
What's already on the hard disk, if anything?

Instead of clicking 'install', click 'try ubuntu without any change to your computer'. When it's booted, open a terminal window and type
```
sudo fdisk -l
```
and post the results here, in [ code ] [ /code ] tags.

---

### Post by sweetandsour on 2010-12-05
> **SecretCode said:**
> What's already on the hard disk, if anything?

Instead of clicking 'install', click 'try ubuntu without any change to your computer'. When it's booted, open a terminal window and type
```
sudo fdisk -l
```and post the results here, in [ code ] [ /code ] tags.

Even i have the same problem...

my hard disk is not being detected...:(

ubuntu@ubuntu:~$ sudo fdisk -l
ubuntu@ubuntu:~$

this is what i get in terminal...

---

