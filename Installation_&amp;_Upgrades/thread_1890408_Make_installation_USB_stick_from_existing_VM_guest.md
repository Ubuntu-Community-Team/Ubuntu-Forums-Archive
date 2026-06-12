---
title: "Make installation USB stick from existing VM guest?"
date: 2011-12-03
forum: Installation &amp; Upgrades
---

### Post by brec on 2011-12-03
Backstory:  I'm new to Ubuntu and Linux, but not to systems software.    In a week or so I'll be completing a new home-built AMD64 hardware platform including an out-of-the-box (empty) hard disk; I intend to run Ubuntu Desktop 11.10 on it.  I currently have a MacBook Pro and Parallels Desktop with which I can install Ubuntu.  I'd like to spend the week or so learning Ubuntu, installing various packages, altering config files, etc.

So, given an 11.10 VM guest system on the MacBook Pro, will I be able to create a bootable USB stick that would (a) allow installation on the new hardware, and (b) retain the additions and changes made on the VM guest?

---

### Post by BC59 on 2011-12-03
It's not very clear what you want to do. So you like to install ubuntu in a Virtual Machine on a Mac and then clone the installation and use it to make other similar ones?

---

### Post by brec on 2011-12-03
> **BC59 said:**
> It's not very clear what you want to do. So you like to install ubuntu in a Virtual Machine on a Mac and then clone the installation and use it to make other similar ones?
Basically, yes.  There will be only one other one, the new hardware I'll have in a week or so, which will be/look different (i.e., possibly require different device drivers) than the VM environment.

I know I can install Ubuntu in a VM from the ISO I've downloaded, and I know I can make a USB stick from that ISO with which I can boot my new hardware and install a virgin Ubuntu on it.  The question is: can make a USB stick like that which will incorporate/retain the post-installation changes I make to the VM-based system.

Possibly clearer:  can I port an existing Ubuntu installation to new hardware via a USB stick?

---

### Post by oldtimer7777 on 2011-12-03
What I would do is install Remastersys on the guest VM and create a backup with remastersys on the guest.  Use Startup Disc Creator to take that ISO you made with Remastersys and create a Live Bootable USB Flash Drive of your Guest System that you can -then- install on whatever computer you want by booting from that USB Flash Stick of Custom Ubuntu.  Enjoy.

Make sure you use the Remastersys Backup option and not Dist.

> **brec said:**
> Backstory:  I'm new to Ubuntu and Linux, but not to systems software.    In a week or so I'll be completing a new home-built AMD64 hardware platform including an out-of-the-box (empty) hard disk; I intend to run Ubuntu Desktop 11.10 on it.  I currently have a MacBook Pro and Parallels Desktop with which I can install Ubuntu.  I'd like to spend the week or so learning Ubuntu, installing various packages, altering config files, etc.

So, given an 11.10 VM guest system on the MacBook Pro, will I be able to create a bootable USB stick that would (a) allow installation on the new hardware, and (b) retain the additions and changes made on the VM guest?

---

### Post by brec on 2011-12-03
> **oldtimer7777 said:**
> What I would do is install Remastersys on the guest VM and create a backup with remastersys on the guest.  Use Startup Disc Creator to take that ISO you made with Remastersys and create a Live Bootable USB Flash Drive of your Guest System that you can -then- install on whatever computer you want by booting from that USB Flash Stick of Custom Ubuntu.  Enjoy.

Make sure you use the Remastersys Backup option and not Dist.
Perfect!

Thanks!

---

### Post by oldtimer7777 on 2011-12-03
> **brec said:**
> Perfect!

Thanks!

You may have to play around with Remastersys for a while until you get the hang of it.  Make sure you don't have anything else running when you are trying to build the custom iso file.  It is very important that you dedicate as much resources as possible to Remastersys so data errors will not develop during the backup using Remastersys. It is very resource hungry.

---

