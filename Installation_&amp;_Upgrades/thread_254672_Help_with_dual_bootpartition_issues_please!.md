---
title: "Help with dual boot/partition issues please!"
date: 2006-09-10
forum: Installation &amp; Upgrades
---

### Post by rowingj on 2006-09-10
I'm not as Linux savvy as I'm aiming to be yet, but I'm having troubles with Ubuntu/XP and am hoping someone can help!

I can boot into Ubuntu, but it goes through all this craziness about hdas 
and errors (like a dos screen, black and white) between when the pretty
Ubuntu screen first shoes and when the login screen pops up. This happens when "Checking all filesystems" comes up. 

When I try to boot XP, it won't. I get this:

Booting 'microsoft Windows, xp professional'

root, (hdd,0)
 Filesystem type unknown, partition type 0x7
savedefault
makeactive
chainloader +1

A disk read error occurred
Press Ctrl+Alt+Del to restart

Also, I can't even access the Windows partition - and when I booted into Linux, where the system icon would be to access my windows stuff wasn't there (still isn't, there's a space where it should be!).

Any suggestions? I need access to XP to finish posters for a conference by Thurs. At this point, it looks like my only option is to re-image it with XP, then re-partition and re-install Ubuntu.

---

### Post by confused57 on 2006-09-10
In Ubuntu, open a terminal(Applications---Accessories---Terminal) and enter:
```
sudo fdisk -l
```
The -l is a small "L".

Post the output of this command...it'll show your partition tables and maybe help determine the entry in your /boot/grub/menu.lst to boot Windows.  Any other information you can give about your system and how you installed Ubuntu will be helpful, also.

---

### Post by oswaldkelso on 2006-09-10
sorry to que jump but we have a similar problem.

[http://ubuntuforums.org/showthread.php?t=254676]("http://ubuntuforums.org/showthread.php?t=254676")

here is our fdisk printout

baztard@baztard-desktop:~$ sudo fdisk -l
Password:

Disk /dev/hda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         784     6291456   1b  Hidden W95 FAT32
/dev/hda2             785       16362   125130285    7  HPFS/NTFS
/dev/hda3           16363       24038    61657470   83  Linux
/dev/hda4           24039       24321     2273197+   5  Extended
/dev/hda5           24039       24321     2273166   82  Linux swap / Solaris
baztard@baztard-desktop:~$

Something has come to mind with ref to thread254676 my friend with the panasonic where we successfully installed ubuntu had xp install disks and this pc has them preloaded??

---

### Post by rowingj on 2006-09-11
> **confused57 said:**
> In Ubuntu, open a terminal(Applications---Accessories---Terminal) and enter:
```
sudo fdisk -l
```
The -l is a small "L".
Post the output of this command...
Output: Unable to open l

> **confused57 said:**
> Any other information you can give about your system and how you installed Ubuntu will be helpful, also.
I'd reimaged (basically reinstalled XP) about 2 weeks before partitioning and installing Ubuntu. My friend did it for me - and I do recall initially there were some issues with partitioning. If you have any specific questions please let me know and I'll ask him. I can't get him to fix this for me, since he's in MA and I'm in NY. Thanks :)

---

