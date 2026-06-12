---
title: "How do i activate nvidia drivers while jockey-kde is broken"
date: 2010-03-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by roger99 on 2010-03-23
Hi all,

Yesterday i decided to give kubuntu a try as KDE 4 is starting to shape up quite nicely now it has had some more dev time.

So i grabbed the iso and proceded to replace ubuntu 10.4 beta with kubuntu.

The first thing i did was install all available updates then went onto install the nvidia drivers.

It seems like the latest updates have broken jockey-kde ( I've been to launchpad and put my tag on an allready open bug, so i'm sure it will be fixed soon ) so I proceded into the kde package manager and installed the nvidia-common packages.

But when i reboot, no nvidia drivers, How do i "activate" the drivers without jockey?

---

### Post by dino99 on 2010-03-23
That is the bug , we have to wait for jockey update. If you open xorg.conf, have you nvidia as driver ?

Nvidia-current normally work but jockey is blind.

---

### Post by roger99 on 2010-03-23
thanks for the reply.

Have been away from linux for a while now cause of having to use windows :sad: a lot for work.  

Atm i have no xorg.conf in /etc/X11 (where it used to reside b4 xorg stopped needing it i presume the path hasn't changed?) and was wondering if jockey would just do a dpkg --reconfigure somewhere along the line, sorry, my memory is vague on the exact command atm.

I will have a go at creating an xorg.conf file.

---

### Post by dino99 on 2010-03-23
try nvidia -xconfig into console

with synaptic, which video packages are installed ?
is your resolution as expected ?

sorry i'm not sure about KDE as i use Gnome, but xorg.conf is no more needed if you dont have multi configs (LCDs, TV, ...)

---

### Post by roger99 on 2010-03-23
I have no secondary display etc, just my lappy :)

nvidia -xconfig just returns command not found.

My resoloution is good in the panels native 1680x1050.

The packages i have installed relating to nvidia, acording to KPackageKit are, nvidia-current, nvidia-current-modaliases & nvidia settings.


EDIT: Sorry, i put a space in nividia-xconfig (duh) will reboot to test the new xorg.conf

---

### Post by dino99 on 2010-03-23
Well, everything is fine, dont worry  :D

---

### Post by plun on 2010-03-23
Seems to be solved but this is the terminal way for Jockey.

list drivers:

```
sudo jockey-text -l
```


enable current driver

```
sudo jockey-text -e xorg:nvidia-current
```


;)

---

### Post by roger99 on 2010-03-23
That solved it, thanks a lot :p

---

### Post by ankspo71 on 2010-03-24
What rotten timing I have. :p I could have used this info an hour ago lol.
I installed jockey-gtk to apply my drivers, then removed jockey-gtk afterwards. I agreed/confirmed to the bug on launchpad for jockey-kde though, which is still installed, and still broken of course.

---

### Post by dino99 on 2010-03-24
> **plun said:**
> Seems to be solved but this is the terminal way for Jockey.

list drivers:

```
sudo jockey-text -l
```


enable current driver

```
sudo jockey-text -e xorg:nvidia-current
```


;)

Have ran these cmd but nothing new: still activated but not used.

---

