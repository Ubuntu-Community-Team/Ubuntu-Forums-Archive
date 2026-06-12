---
title: "help!! GRUB error 21"
date: 2005-03-15
forum: Installation &amp; Upgrades
---

### Post by acada on 2005-03-15
Hi!!
At the boot I get an error 21 and GRUB crashes!! I don't know what to do!! The summary of my failed installation follows.

I have Windows Xp on my pc at home and installed Ubuntu on a second hard drive, hdb.
The installation seemed to went fine (apart from the internet connection since I still use modem). At the moment of installing GRUB, the program recognised that I had Windows on the computer. I installed GRUB on /dev/hdb2.
At the first reboot, GRUB crashed with no words.
I reinstalled everything on the same hard disk. The master hard drive still had the right format. But this time no other operative systems were recognised on the computer!! I installed GRUB on hb0 now, since I thought that might have been the problem. Now I get Error 21 when GRUB starts! It is therefore impossible to boot into the system!! My girlfriend will soon kill me!! :lol: 

Anyone can help?
thanks in advance!!
cada

---

### Post by az on 2005-03-15
21 : Selected disk does not exist
     This error is returned if the device part of a device- or full file
     name refers to a disk or BIOS device that is not present or not
     recognized by the BIOS in the system. 


Right.  Grub uses bios to detect drives and your bios is confusing grub.  I am not saying that you have broken hardware, just that grub is confused,

Generally, it is better to install grub on /dev/hda0

Anyway, can you boot into bios and change the boot order to boot from hdb first?  Maybe you will go right into ubuntu and you can fix things.


If that does not work, maybe you can boot into a live cd and remove grub?

sudo dd if=/dev/zero of=/dev/hda bs=446 count=1


"My girlfriend will soon kill me!!"

"Sorry, honey.  I know Windows is _there_.  I just need  little time to get to it.  Just use linux for a while while I work on it."  (been there...)

---

### Post by acada on 2005-03-15
thanks! I will try to use knoppix to boot and remove Grub with the command you told me. I expect that after the removal Windows will start automatically at the reboot. Is it correct?

---

### Post by az on 2005-03-15
I hope so.  It would be safer to try to boot ubuntu and reinstall grub properly.

---

### Post by lao_V on 2005-03-15
I always thought it was safest to install any bootloader in the MBR which is autodetected by BIOS and thus should not have any problem when having multiple hd/partitions

---

