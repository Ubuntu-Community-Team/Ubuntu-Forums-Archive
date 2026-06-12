---
title: "Multi-boot: upgrade to Windows 10?"
date: 2015-11-13
forum: Installation &amp; Upgrades
---

### Post by 2CV67 on 2015-11-13
I am currently multi-booting 15.04 with 14.04LTS & Windows 8.1.
I need to keep Windows for a few odd jobs which Ubuntu can't do, like updating my TomTom GPS.
Sooner or later, I suppose I will (from choice or not) upgrade to Windows 10.

Can anybody tell me what the consequences are likely to be, particularly for the initial reboot after that upgrade?
Will Windows take charge of booting?
And hide Ubuntu?

What is the best solution?

I imagine having to use SuperGrub2Disk on a USB stick to find Ubuntu?
Then get control of Grub via "sudo update-grub" & "sudo grub-install /dev/sda".

Or am I worrying for nothing?

Thanks!

---

### Post by grahammechanical on 2015-11-13
You are right to worry. From the first day that upgrades to Windows 10 became available people have been posting on this forum about their problems caused by running the upgrade.

It seems certain that Windows 10 will take over the OS boot loading process. You will need to find a way to load Ubuntu and run those 2 Grub commands. Another way would be to run a Ubuntu live session, install Boot Repair, let it produce a report and after examining the recommend repair option to let Boot Repair re-install Grub. Which seems to be one of the things that Boot Repairs recommends in these situations.

Regards.

---

### Post by sammiev on 2015-11-13
+1 to post number 2.

I also found that after updating to Windows 10, you maybe better off to make a boot-able recovery of Windows and do a fresh install.

Windows 10 seem to run better from the fresh install than from the upgrade.

---

### Post by oldfred on 2015-11-13
If it is UEFI, you still should have the ubuntu entry in UEFI. Windows will make its entry first in boot order, but will not overwrite the ubuntu folder in the ESP - efi system partition.
If a system that let you boot ubuntu without a work around then you should just be able to set ubuntu as first in boot order again with either UEFI or efibootmgr.

But you need to turn off the fast start up or always on hibernation again.

---

### Post by 2CV67 on 2016-03-03
Well I finally upgraded from W8.1 to W10 and everything went OK with no special actions required!

The grub screen stayed exactly as before & booting to 15.10 & 14.04LTS & W10 (bottom of list) was straightforward.

Simpler than upgrading Ubuntu from 15.04 to 15.10.....

At first glance W10 is a lot less bad than W8.1 too, though I will only be using it for stuff Ubuntu can't do (updating TomTom GPS etc).

I'll call this one [SOLVED].

---

