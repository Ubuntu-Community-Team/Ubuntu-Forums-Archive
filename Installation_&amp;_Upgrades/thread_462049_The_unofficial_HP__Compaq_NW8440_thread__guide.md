---
title: "The unofficial HP / Compaq NW8440 thread / guide"
date: 2007-06-02
forum: Installation &amp; Upgrades
---

### Post by Rocketeer on 2007-06-02
[Updated: 2nd June 16:53]

Hi everyone,
just wanted to share my experiences for the installation of Ubuntu (Feisty) on a HP / Compaq nw8440.

Installation by Live CD is working until the software wants to start the X Server. There's an error. Solution for this problem was to do the following [internet connection required!]

```
sudo apt-get update
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --initial
startx

```
=> Install Ubuntu on desired HD

After reboot you will see that X does not start (...again). This is because the driver was not installed. So simply install the driver again:

```
sudo apt-get install xorg-driver-fglrx
startx
```

=> do some updates and reboot again - here we go. you are all set (as far as i know).

---

### Post by pfrancav on 2007-06-10
Hi, nice trick, really thank, this work for me but I've another problem with this laptop that I can't resolve.

I've installed Feisty with dual boot, I mean that I keep my original Windows Xp installed and I add Feisty in another partiton.

After install, I login Feisty ok, later I login in Windows, and when I reboot, the machine enter in a infinity loop rebooting his self.

I reinstalled Ubuntu again, and I've the same problem, I reinstalled with Dapper and the same problem again, seems like after login in windows, Grub crashs and I can't enter any of both.

Anybody Install Dual boot in this machine ?, any idea?

Thanks

PD: I've a Toshiba with dual boot and no problem.

---

### Post by Rocketeer on 2007-06-12
Hi there, I am not sure if this is a problem of the nw8440 itself but a problem with the installation order and/or partitions...

I know there are problems when you try to install to an external harddrive, but normally there should be no problem when installing windows XP first and then ubuntu, because ubuntu see XP and adds it to the boot manager list.

Maybe you should open an own thread with your problem due to the fact it is probably not an NW8440 issue.

---

### Post by pfrancav on 2007-06-13
Hi, I think that is a NW8440 problem, I've installed a few of machines with XP and Ubuntu, and never have this problem...

Seems like there is a factory protection, look at this:

[http://translate.google.com/translate?u=http%3A%2F%2Fdoc.ubuntu-fr.org%2Fwindows%2Fpc_tatoue&langpair=fr%7Cen&hl=en&ie=UTF-8&oe=UTF-8&prev=%2Flanguage_tools](http://translate.google.com/translate?u=http%3A%2F%2Fdoc.ubuntu-fr.org%2Fwindows%2Fpc_tatoue&langpair=fr%7Cen&hl=en&ie=UTF-8&oe=UTF-8&prev=%2Flanguage_tools)

Have you ever install Ubuntu in dual boot mode in this laptop?

Thanks !

---

### Post by Rocketeer on 2007-06-15
no, but a friend did. I will call him in for assistance...

---

### Post by ping_ch on 2007-06-15
I've installed winxp pro and feisty on my nw8440 without problems.

Booting and rebooting  works in every case so far, but maybe it has to do with your partitions or something. 
I installed everything in this order:
1. installed win xp pro (oem)
2. re-partitioned the disk using PartitionMagic to have partition 1(ntfs): winxp, partition 2: linux swap, part3(ext3): feisty
3. installed  feisty

---

### Post by pfrancav on 2007-06-15
Hi, Ping_ch, I installed exactly like you, in this order, and I have done 3 times.

Whatever, if any have the same problem, this is the solution that work for me:

1) Install XP (OEM)
2) Use Partition Magic
3) Install Ubuntu, but don't install grub in MBR, install in the linux partition
4) Restart in Windows and use "bootpart" to add NTLDR (Windows bootloader) the Ubuntu SO

a better explain in the first post in this thread:
[http://ubuntuforums.org/showthread.php?t=80508](http://ubuntuforums.org/showthread.php?t=80508) 

I hope this help

Thanks to all !

---

