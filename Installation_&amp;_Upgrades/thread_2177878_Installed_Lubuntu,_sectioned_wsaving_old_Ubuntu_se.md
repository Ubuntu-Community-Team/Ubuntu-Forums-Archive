---
title: "Installed Lubuntu, sectioned w/saving old Ubuntu section, can't find it to log in...?"
date: 2013-09-30
forum: Installation &amp; Upgrades
---

### Post by secuono on 2013-09-30
So I had Ubuntu, when I was installing Lubuntu, it asked me if I wanted to save all the Ubuntu stuff and be able to log into it and the new Lubuntu. I agreed. Now I cannot find a way to get to the old Ubuntu....
Where is it, how do I reach it?
When I shut down and power on, a black screen shows with several things listed, something like Ubuntu first and then a bunch of other options all mentioning Ubuntu. If I click anything or not make a choice, it takes me to the Lubuntu log in page. 
...So, where did I go wrong?


[[[sorry for all the Qs]]]

---

### Post by Bashing-om on 2013-09-30
secuono; Hi !

Don't recon you have done anything wrong.
Simple thing first.

What results if you choose a different option than the first boot option - non recovery.

If still with a problem:
show us the out put of terminal codes:
```

sudo fdisk -lu
sudo parted -l from
sudo parted /dev/sda unit s print
lsblk -f

```
which shows the disk(s) partitioning info.

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by secuono on 2013-10-01
Thanks! =D
There are several and I should of realized the one with my version number next to it would be the Ubuntu I needed! Weird thing is that the first Ubuntu listed has no version number and is actually to get to Lubuntu....Don't know why it doesn't add the L.
ubuntu
memory test
memory test
ubuntu 8.4
advanced options for ubuntu 8.4

---

### Post by Bashing-om on 2013-10-01
secuono; Welp;

All versions have the same kernel - ubuntu -
As to the 1st boot nomenclature, I too am mistified. I was in the process of upgrading Lubuntu 12.04 and it failed (mirror fault) and has messed up my beautiful grub menu. Will fix it when I get that upgrade completed.
Presently I too only have the entry "ubuntu" to boot Lubuntu. When I know more I will relay what I learn.

Be aware that the grub boot menu is highly configurable and customizable  - if one cares for the esthetics.

[INDENT][INDENT]all things can happen to the good
[/INDENT][/INDENT]

---

### Post by secuono on 2013-10-01
> **Bashing-om said:**
> 

Be aware that the grub boot menu is highly configurable and customizable  - if one cares for the esthetics.


Probably tricky and don't want to screw anything up...don't really mind an ugly or weird boot menu, not like I stare at it for very long. =)

thanks for all the help

---

### Post by Bashing-om on 2013-10-01
secuono;

You are quite welcome, pleased to share.

Simpler is always better in my view. However, I am at a minimum triple booting.. and my grub menu can get to be almost unmanageable in the default configurations. I have had to learn a lot about grub .. and believe me, as in all things ubuntu, I still have more to learn.


If you are satisfied that your question is completed to your satisfaction, please mark this thread as solved. -aids others seeking a solution and helps keep the forum tidy -.

[INDENT][INDENT]happy trails to you
[/INDENT][/INDENT]

---

### Post by secuono on 2013-10-01
> **Bashing-om said:**
> 

If you are satisfied that your question is completed to your satisfaction, please mark this thread as solved. -aids others seeking a solution and helps keep the forum tidy -.]


It was already marked as solved over an hour ago. 
=)

---

