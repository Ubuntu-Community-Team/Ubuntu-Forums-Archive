---
title: "Two Hard Drive Installation"
date: 2008-05-24
forum: Installation &amp; Upgrades
---

### Post by timofthec on 2008-05-24
Hi all,

I currently have ubuntu dual booting with xp on one partitioned hard drive.  I want to change that to have xp on a master drive and ubuntu on a slave drive (ide) and retain the dual booting option.

Now, I planned to start this today and read a very good guide on how to do this earlier in the week.  However, like a prat I did not print the instructions or note the name of the thread and now, after 45 minutes of searching, I cannot get back to the guide :(

Can anyone either point me in the right direction or let me hafcve some tips on dual booting with two HDDs?

---

### Post by rbrick49 on 2008-05-24
hi I have a triple boot working with vista,ubuntu and mandriva just load xp on master and ubuntu on slave in that order and ubuntu will load its boot loader it will reboot and all yo do is select which operating system you want

---

### Post by timofthec on 2008-05-24
Thnx for the reply rbrick.

My plan is to reload xp onto the master and have ubuntu on the slave.  Is it as simple as simply doing xp first and then ubuntu, making sure I set the destination for ubuntu as the slave drive?  Will grub still work like that or do I have to amend it?

---

### Post by bobblehat on 2008-05-24
If you're going to do a complete clean install (it sounds like you are) you can just reinstall XP over one drive, then install Ubuntu and select the second drive in the partitioning options (it'll come up as something like 'guided - use entire disk ....').

---

### Post by cdtech on 2008-05-24
I did mine as a dual boot, rather than having Ubuntu install the Bootloader on the primary disk I declined and installed it on the Ubuntu disk. The way I boot is to select the drive order during the computer bootup (selecting f9).

This way I have no problems with my MBR within my Vista OS and both are independent of each other.

Just some advice....

---

### Post by timofthec on 2008-05-24
> **bobblehat said:**
> If you're going to do a complete clean install (it sounds like you are) you can just reinstall XP over one drive, then install Ubuntu and select the second drive in the partitioning options (it'll come up as something like 'guided - use entire disk ....').

Yep, bobble, that's the plan.  XP has gotten to the stage where I like to do a fresh install to get rid of the bloated crap on it + I want to upgrade ubuntu to the latest release.  Have acquired a 60ghb hard drive as well and so want to separate them on to their own drives.

> **cdtech said:**
> I did mine as a dual boot, rather than having Ubuntu install the Bootloader on the primary disk I declined and installed it on the Ubuntu disk. The way I boot is to select the drive order during the computer bootup (selecting f9).

This way I have no problems with my MBR within my Vista OS and both are independent of each other.

Just some advice....

Thnx CD - a quick question though - if you don't press f9, will the computer default to windows?  The reason I ask is that the rest of the family will still use xp and I need it to be the default OS.

---

### Post by cdtech on 2008-05-24
Yes, it will default to the primary hard drive that you set up within your bios.

---

### Post by timofthec on 2008-05-24
ok, many thnx, logging off now to break me computer :)

---

### Post by cdtech on 2008-05-24
LOL!!

Good Luck........

---

### Post by timofthec on 2008-05-24
ok guys - many thnx for the info, I'm all freshly installed without a hitch - xp on the primary drive and ubuntu on the slave :)  Just got lots of applications to install now :(

I have come across a situation that I didn't expect though - Grub is still there.  It's not a problem (apart from I've got to work how to amend the menu) but I expected the XP installation to overwrite grub.

Anyway, thnx again.

---

