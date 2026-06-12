---
title: "Need help with Ubuntu Install to new HDD onto existing Windows XP RAID system"
date: 2007-06-07
forum: Installation &amp; Upgrades
---

### Post by andystar on 2007-06-07
Hi,

I recently came across Ubuntu and am currently trying to get it installed on my existing Windows XP machine and allow me to dual boot into either OS.  I'm a newbie to linux system level stuff (but use linux at work) so I'm not very knowledgeable in the system area yet.  So far I have Ubuntu up and running, however **[COLOR="Blue"]I'm still a little confused about configuring for dual boot and could use some descriptive help[/COLOR]**.  I've read a bunch of posts on the forums, but haven't found out how/what to modify in order to dual boot.  Any help is greatly appreciated.

**My 2nd install of Fiesty went as follows:**
    1) Windows XP as RAID (two-100GB drives)
    2) Installed new HDD as only drive (disconnected my Windows RAID HDDs)
    3) Installed Linux on new HDD (two partitions, first is for /home, second is for linux root "/")
    4) Set Linux HDD as primary boot in BIOS
    5) Reconnected my Windows XP RAID HDDs
    6) Did not Install Fiesty Kernel updates (a lot of forum posts indicate an issue with it)
    7) My system default boots to Ubuntu, with no GRUB option for Windows

Note: my first install, I left the Windows drives hooked up and Ubuntu put GRUB in my Windows MBR, causing me lots of headaches:(.  On my following Ubuntu install I disconnected my Windows HDDs (read to do this on a post).

I believe I can't boot to Windows because my /boot/grub/menu.lst file is missing my Windows RAID HDD entries (due to not having them hooked up during install), and maybe my /boot/grub/device.map and /etc/fstab file need updating.

**At this stage I have two questions:**
1) Will reinstalling Ubuntu with my Windows HDDs hooked up (ubuntu HDD as primary boot during install) provide dual-boot capability without any modifications?  (Will this put ubuntu in my Windows MBT cause I don't want it there)
2) If its possible for my current install to recognize Windows and give me the boot option at startup, can someone provide guidance in what I need to modify?

**System Information:**
I've pasted output from commands that give system device information (fdisk -l, blkid).  Being an Ubuntu newbie, I don't understand everything they tell me.  Because of this I'm not able to determine what  to change in order to be able to select my boot OS at startup.

*andrew@Ngai:~$ sudo blkid*
/dev/sda2: UUID="6c152ac8-bf48-475c-b6e0-dafc80a7bed3" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda3: UUID="c49e83f4-8e23-468e-b7f8-aebec79c89ac" TYPE="swap" 
/dev/sda5: UUID="7d9573b5-06dc-4f02-9d53-59a122b59738" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hda1: TYPE="ntfs" 
/dev/hdc1: TYPE="ntfs" 

*andrew@Ngai:~$ sudo fdisk -l*

Disk /dev/hda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14946   120053713+   7  HPFS/NTFS

Disk /dev/sda: 30.8 GB, 30839584768 bytes
255 heads, 63 sectors/track, 3749 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2188    17575078+   5  Extended
[COLOR="Red"]**/dev/sda2            2189        3525    10739452+  83  Linux**[/COLOR]
/dev/sda3            3526        3749     1799280   82  Linux swap / Solaris
/dev/sda5               1        2188    17575047   83  Linux

Disk /dev/hdc: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1       14946   120053713+   7  HPFS/NTFS

I noticed my /boot/grub/menu.lst contains the UUID for /dev/sda2, which is my root linux directory, but the line has a comment "#" character at the beginning.  I'm not clear if the UUID is used in this file.

So, can anyone help me out?  Please be very descriptive.

Much appreciated,
Andrew

---

### Post by confused57 on 2007-06-07
I'm not familiar with Raid configurations, but you might try this to boot Windows from grub...in Ubuntu, open a terminal(Applications---Accessories---Terminal), edit your menu.lst:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```

Add an entry similar to this at the very bottom of the menu.lst file:
```
title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1
```
quit & save

You'll probably need to set your Ubuntu drive as the first hard drive booted, then set your Window's drive(1st drive in your Raid?) to boot second...

---

