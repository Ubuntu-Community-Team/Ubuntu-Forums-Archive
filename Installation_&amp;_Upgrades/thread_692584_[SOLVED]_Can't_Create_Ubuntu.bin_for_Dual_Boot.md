---
title: "[SOLVED] Can't Create Ubuntu.bin for Dual Boot"
date: 2008-02-09
forum: Installation &amp; Upgrades
---

### Post by TrendRat on 2008-02-09
Hello, N00b here

I'm working on getting my P4 2.4 GHz pc to dual boot XP and Ubuntu.  I'm close, and I'll spare you the details of the pain it took to get to this point.  Suffice it to say most of it was self-inflicted and I like the idea of a free, non-windows OS, so it's all good.  

My PC has 3 hard drives, two in a raid 0 array with XP installed.  The third hard drive now has Ubuntu 7.1 installed; I used the alternate cd as I had issues with my Matrox Parhelia vid card and the Live CD.  The Ubuntu drive has 3 partitions; a 50 GB ext3 bootable partition with Ubuntu 7.1 on it, a swap partition, and a 268 GB /share partition formatted with ext3.  I did not make the share partition FAT32 as I installed the Ext2 Installable File System for Windows.

I did not modify the windows mbr file with grub, so the machine boots up in XP just fine.  I have read the excellent thread at [http://www.linuxdevcenter.com/lpt/a/6554](http://www.linuxdevcenter.com/lpt/a/6554) on how to create a dual boot machine, as well as others.  

But I am having problems creating the ubuntu.bin file.  When I boot with the Linux System Rescue CD, gparted cannot find any of my devices.  It scanned for several hours and did not find them.  So even if I do create the ubuntu.bin file, I have nowhere to store it.  As far as I can tell, the only devices the Rescue CD identifies are my cdrom and dvd drives (kinda hard to tell as everything flashes by so fast during bootup).

Any ideas on creating ubuntu.bin, getting it on my windows drive, and finding my devices would be greatly appreciated.

---

### Post by TrendRat on 2008-02-10
I decided to reinstall ubuntu and repartition the drive to see if this would solve the problem with the Rescue CD not seeing my devices.  It did.  After the install, I shutdown ubuntu and rebooted directly from the Rescue CD without letting XP boot.  I started gparted and it scanned and found all my decives.  I was able to create and write ubuntu.bin to the shared driive.  

My drive partitions are:

SCSI6 (0,0,0) (sdc) 320.1 GB Seagate ATA ST3320620AS
 #1 primary    1.0 GB      f     swap     swap
 #2 primary  50.0 GB  B  f     ext3       /
 #3 primary 268.1 GB     f     ext3       /share
 #4 primary 962.4 MB     f     swap     swap

However, when I let XP boot and looked for ubuntu.bin, I couldn'd find it.  Windows assigned a drive letter to the first swap partition, but it didn't recognize the format.  I went into My Computer - Manage - Drive Management, but I couldn't assign a drive letter to the /share partion.  Windows file manager would not recognize the /share partition, even tho I had the Ext2 Installable File System installed.

I rebooted from the Rescue CD, started gparted and scanned for devices.  Nada - nyet - no dice - nuthin'.

I'm going to re-install ubuntu from the alternate cd (hopefully for the last time) and make the share partition FAT32, and hope I can get the file then.

---

### Post by confused57 on 2008-02-10
If your bios is capable of booting first to the drive with Ubuntu, you could install grub's IPL to it's mbr, then boot Windows or Ubuntu from grub.  This may be an option, if you're not able to boot Ubuntu from Windows.

---

### Post by TrendRat on 2008-02-10
Thanks, confused57.  I'm feeling confused^2 at the moment.  No, my bios doesn't seem to see this Seagate Sata drive which is connected to a Promise pci raid card.  I will check the links, thanks for listing them.  At the moment, I'm off into forum-land again, to find out why ubuntu refuses to partition/format my /share partition as FAT32.  It just tells me the attempt to format as fat32 failed, and asks if I want to continue partitioning.

---

### Post by TrendRat on 2008-02-10
Confused57:
You were right - I can set my bios to boot from the second drive, and after some messing around, I did that.  Unfortunately it didn't work, saying it couldn't boot from that drive.  This is after installing everything from the alternate cd without any problems.  So I'm guessing there may be some kind of hardware conflict.  Maybe Ubuntu can't deal with my ST Labs Sata & ATA133 PCI Raid Combo Card with Seagate Sata 320 GB drive running in nonraid mode.  I'll check into this next, as I can see no other reason why this shouldn't work.

Thanks for your help.

---

### Post by confused57 on 2008-02-10
> **TrendRat said:**
> Confused57:
You were right - I can set my bios to boot from the second drive, and after some messing around, I did that.  Unfortunately it didn't work, saying it couldn't boot from that drive.  This is after installing everything from the alternate cd without any problems.  So I'm guessing there may be some kind of hardware conflict.  Maybe Ubuntu can't deal with my ST Labs Sata & ATA133 PCI Raid Combo Card with Seagate Sata 320 GB drive running in nonraid mode.  I'll check into this next, as I can see no other reason why this shouldn't work.

Thanks for your help.
If you're not sure that grub was installed to the Ubuntu drive's mbr, you can install it with the Ubuntu live cd:
[http://ubuntuforums.org/showthread.php?t=224351&highlight=live+cd+grub](http://ubuntuforums.org/showthread.php?t=224351&highlight=live+cd+grub)
from the above howto, it should be something like:
```
root (hdx,y)
setup (hdx)
```
see it this gives you a grub boot menu...if it does, highlight your Ubuntu entry, press "e", the highlight the root line, press "e" again, then change root from (hdx,y) to (hd0,y), press "enter", then "b" to boot...y means leave this value as it is.

---

### Post by TrendRat on 2008-02-11
Thanks, confused57, I will give it another try.  I'm pretty sure grub was installed, tho, as I saw a "installing grub" message come up....and no error messages.  But I've been fooled before, and with your detailed help it inspires me to have another go at it....

---

### Post by TrendRat on 2008-02-12
**[SIZE="6"]YAAAAHHHOOOOOOOOOOOOOOOOOOOOOOO!!!!!!!!!!!!!!!!!!!!!!![/SIZE]**  It ACTUALLY booted!!

Crap......now I'm going to have to talk to my wife in the evening.......

Actually, it booted to a command line and it looks as if there are some issues.  It says all my partitions contain file systems with errors, then says FIXED.  Anyway, the GUI started up when I typed in startx, so I'm gonna play for a while.

confused57, may I suggest a name change, please consider 57genius.  Thanks for your help.  :KS

I would imagine I'll have some more questions about how to make XP and Ubuntu live together peacefully, but that will be later.

---

### Post by confused57 on 2008-02-13
> **TrendRat said:**
> **[SIZE="6"]YAAAAHHHOOOOOOOOOOOOOOOOOOOOOOO!!!!!!!!!!!!!!!!!!!!!!![/SIZE]**  It ACTUALLY booted!!

Crap......now I'm going to have to talk to my wife in the evening.......

Actually, it booted to a command line and it looks as if there are some issues.  It says all my partitions contain file systems with errors, then says FIXED.  Anyway, the GUI started up when I typed in startx, so I'm gonna play for a while.

confused57, may I suggest a name change, please consider 57genius.  Thanks for your help.  :KS

I would imagine I'll have some more questions about how to make XP and Ubuntu live together peacefully, but that will be later.

I meant to type in "Confucius57", but got confused & typed it wrong when I was registering for the forum, now I'm stuck with being eternally confused(57, that is).

It's temporary if you used the "e" method to boot into Ubuntu, however you can make it permanent in your menu.lst:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```
Change the root to whatever worked, if you used the "e'" method...also, be sure to change the line with groot to the correct root(leave the # in front of groot)...quit & save.

You may be able to boot Windows from grub, using the entry in this thread:
[http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)
this would work if Windows is on the first partition...second partition would be (hd1,1) for root.

---

### Post by TrendRat on 2008-02-17
confused57, I made the edits to the menu.lst file as you mentioned and now grub boots up as it should, without any help.  Thanks again.

Now I have two more tasks - 1) get windows to see my ubuntu.bin file and work as a proper dual boot machine, so I don't have to enter F2 - Setup every time I want to switch from windows to ubuntu; 2) get my video card situation straightened out.

---

### Post by confused57 on 2008-02-17
> **TrendRat said:**
> confused57, I made the edits to the menu.lst file as you mentioned and now grub boots up as it should, without any help.  Thanks again.

Now I have two more tasks - 1) get windows to see my ubuntu.bin file and work as a proper dual boot machine, so I don't have to enter F2 - Setup every time I want to switch from windows to ubuntu; 2) get my video card situation straightened out.
If it were my system, I would use grub to dualboot with Windows...see the link I provided earlier for editing your menu.lst to add an entry to boot Windows:
[http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

Maybe I'm biased, but I believe grub is much easier to work with than editing boot.ini...here's an excellent guide for using grub:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

