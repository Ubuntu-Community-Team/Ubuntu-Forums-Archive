---
title: "Ubuntu 10.04 an openSUSE boot problem"
date: 2011-03-11
forum: Installation &amp; Upgrades
---

### Post by Dimison on 2011-03-11
I installed yesterday the 11.4 openSUSE to my desktop pC (in my 160hdd that previous had WinVista).
The bad thing was that I used grub from opensuse to be installed to MBR.
openSUSE uses Grub 1.5 and I want grub2.
Now I cannot see Ubuntu when grub legacy loads.

I will post the results from 
```
fdisk -l 
```
later today (cause i am not in my pc)

to give you some informations about my hdd..
I have sda (first boot disk) - With openSUSE right now, previously with win-vista
sdb with Ubuntu 10.04
sdc only for files

My problem is that I want to keep sda first but to place grub2 instead of grub legacy...

---

### Post by Sef on 2011-03-11
Read Ubuntu Documentation [GRUB2]("https://help.ubuntu.com/community/Grub2").

---

### Post by NightwishFan on 2011-03-11
> **Sef said:**
> Read Ubuntu Documentation [GRUB2]("https://help.ubuntu.com/community/Grub2").

RTFM! :lolflag:

---

### Post by Dutch70 on 2011-03-11
*[COLOR="Red"]Edit: The post below is not exactly correct, see the following posts.[/COLOR]*

To the OP, if you install Grub2, you're not going to be able to see openSUSE. Legacy & Grub2 number them differently. Legacy starts at "0" and Grub2 starts at "1". 

e.g. for PCLinuxOS, I had the following in /boot/grub/grub.cfg

```
menuentry "PCLinuxOS-10.12 (on /dev/sda6)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 3f399271-92e3-4683-827d-45125fea0d8c
	linux /boot/vmlinuz BOOT_IMAGE=linux root=UUID=3f399271-92e3-4683-827d-45125fea0d8c resume=UUID=8316ec3c-6153-427c-bb21-884dc8b29de6 splash=silent vga=788
	initrd [COLOR="Red"](hd0,5)[/COLOR]/boot/initrd.img
``` 
I have to change it to (hd0,6) every time I update-grub or I can't log-in to PCLinuxOS. This is something I've just figured out, so I don't have a better workaround. Nor am I very interested in getting one tbh.

_

---

### Post by Quackers on 2011-03-11
I don't know about grub2 picking up PCLinuxOS but it certainly picks up openSUSE on mine.
From the live cd desktop re-install grub2 to the mbr of the drive by first mounting the Ubuntu root partition, then when Ubuntu boots directly open a terminal and run ```
sudo update-grub
``` and watch as grub.cfg is run, to make sure that openSUSE is found. If it is, reboot and look at your shiny new grub menu.
Details here
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by Dutch70 on 2011-03-11
> **Quackers said:**
> I don't know about grub2 picking up PCLinuxOS but it certainly picks up openSUSE on mine.
From the live cd desktop re-install grub2 to the mbr of the drive by first mounting the Ubuntu root partition, then when Ubuntu boots directly open a terminal and run ```
sudo update-grub
``` and watch as grub.cfg is run, to make sure that openSUSE is found. If it is, reboot and look at your shiny new grub menu.
Details here
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

My apologies, I stated that wrong...:oops: 

 As far as PCLinuxOS goes. Grub picks it up & it shows up in my grub menu. It just won't load unless I change that "5" to a "6" as mentioned above. I'm certainly no expert, as you know, you helped me get my system going. However, that was my experience with grub 1.5. 
There may be more going on than I'm aware of. :?

---

### Post by Dimison on 2011-03-11
Thank you for your replies regarding my issue.

I have to say that I already read the Grub2 howto on ubuntu web site. I tried sudo update-grub, grub install to sdb (but my pc has only sda at boot order)

The problem is that when I tried to install on MBR Grub2 (at sda)i got an error regarding "/" and /dev
Something like cannot be mounted...

I am thinking to get rid of openSUSE and install Kubuntu 11.04 alpha3 for test.
This will probably fix my problem cause of Grub2... am i right?

---

### Post by Dimison on 2011-03-11
Results from fdisk -l
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2d2e2d2e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    41945087    20971520   83  Linux
/dev/sda2        41945088   312580095   135317504   83  Linux

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7ad72833

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63    58589054    29294496   83  Linux
/dev/sdb2        58589116   488392064   214901474+   5  Extended
/dev/sdb5        58589118   482528339   211969611   83  Linux
/dev/sdb6       482528403   488392064     2931831   82  Linux swap / Solaris

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x270a5521

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   976773166   488386552    7  HPFS/NTFS/exFAT

```

---

### Post by Quackers on 2011-03-11
If sda is the only bootable hard drive in your bios, then grub2 needs to be installed there to work.
Have you seen this guide, by drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

Dutch70, I'm not sure what's wrong there, but something is not right. Have you checked /etc/fstab entries for the PCLinuxOS - both UUID and /dev/sdX

---

### Post by Quackers on 2011-03-11
Dimison, please boot into Ubuntu and then go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by oldfred on 2011-03-11
I have seen Dutch's issue on several Linux versions with old grub legacy. Once the set root is used, you do not have to preface the kernel & initrd boot lines with (X,Y) entries. So I think the os prober just copies those menu entries from old grub & renumbers just the set root. It does not expect to have to renumber the kernel & init lines as it does for the set root line. One fix is just to remove the (X,Y) entries in menu.lst in grub legacy. It will still work. One other is just to copy entry to 40_custom, edit there and only have to re-edit on new kernels.

---

### Post by Dimison on 2011-03-11
There is a general issue with openSUSE and i discard it.
I placed a kubuntu installation and grub2 now is installed on sda so i am back to business!

Thank you for your time!

---

### Post by Quackers on 2011-03-11
You're welcome. I'm happy to hear you've sorted things out.

---

