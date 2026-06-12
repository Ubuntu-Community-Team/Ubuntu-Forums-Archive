---
title: "GRUB on diff disk how?"
date: 2005-02-28
forum: Installation &amp; Upgrades
---

### Post by sz3n on 2005-02-28
Hi I have winxp pro on  my c drive which is my primary disk. I wanted to install Ubuntu on  another drive in my system other then my primary drive ..so far no problem with that .... 

But I  do not want to install  GRUB on my primary  windows drive which is C ... I installed in on my D drive.  hoping that when i reconfigure my bios to boot D drive first it will launch GRUB and let me choose which operating system to launch.  This does not seem to work ...?   

The reason i did not want grub  to be installed on my windows C drive MBR to mess it up in anyway.


Does this all make sense  can anyone help me..?

 :-?

---

### Post by Bunta on 2005-02-28
Yes, I know what you are talking about.

My installation scnenario is the same as you but I had GRUB installed on C(primary drive with XP). This totally messed up my MBR. So when I turn on my computer and GRUB loaded and I choose Window XP, I get this error : Unmountable disk Volume. However, when I boot into ubuntu, ubuntu works fine. To get my window XP to work, i had to fixmbr and that overwrite and kill GRUB.

Anyway, try to load GRUB on C: and see what happened. If you get the same problem as me, you can always use fixmbr to get window back.

---

### Post by amrust on 2005-07-13
If you used fixmbr to get Windows XP booting again, how do you then boot Ubuntu?

---

### Post by kevinwh on 2005-08-25
I am experiencing this issue as well, but I am installing ubuntu on a separate partition of a single disk.  Any headway on this issue?

---

### Post by kevinwh on 2005-08-25
[http://enterprise.linux.com/enterprise/05/02/16/1919205.shtml?tid=129&tid=49](http://enterprise.linux.com/enterprise/05/02/16/1919205.shtml?tid=129&tid=49)

This article may help those of you installing on two separate hard disks.  But my problem on a single disk/separate partition scenario remains...  Anybody have ay ideas?

---

### Post by Zyrix on 2005-11-02
I'm not sure if this is related to the original issue or not. But here is my situation:

I have 1 drive (30GB). It had Windows XP on 20GB of it, the extra 10GB was free. 

I installed Ubuntu to the 10GB partition (with default partition ext3 and swap) and wrote grub to the MBR. When I boot the machine I get a Grub menu to choose XP or Ubuntu. If i load Ubuntu everything is fine. When I boot Windows I get Unmountable Boot Volume - bluescreen of death. 

So I wipe everything and reinstall Windows (it was a clean install anyways) on a 20GB partition. 

Then I install Ubuntu on the additional 10GB of free space on the drive and partition it as follows:

hda1 - Windows -  NTFS - 20GB
hda2 - /boot - ext2 - 32MB
hda3 - / - reiserfs - 9GB
hda4 - swap - 512MB

I then installed Grub to hda2

When I boot it goes straight into Kubuntu. So from there I edit the /boot/grub/menu.lst and add the following:

title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


I reboot the machine and load Windows and get the same BSOD: UNMOUNTABLE_BOOT_VOLUME

Anyone have any advise?

---

