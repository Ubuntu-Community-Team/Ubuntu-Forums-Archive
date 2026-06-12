---
title: "[SOLVED] grub move from one hdd to another"
date: 2008-10-16
forum: Installation &amp; Upgrades
---

### Post by aaronp on 2008-10-16
Hi all,

I previously had two hard drives, with multiple partitions. One hard drive (I'll call it A) was running WinXP and another (B) running Ubuntu.
Hard drive A died (good in a way because it forced me to take the leap from Windows that I'd been thinking about) and was thrown away and I got a new hard drive (C) to replace it. I was running with just Ubuntu on drive B for a while, using C for extra storage and I did a few tricky (dumb) things and stuffed up my installation on B.

So I decided to put a fresh install of Hardy on to the new drive C which is my current live installation and is working a treat for me.

My problem is, I want to free up the space on B but the grub which allows me to boot into my current installation of Ubuntu on C is sitting on drive B.
I have had some issues trying to move grub before and am apprehensive about trying it again and wrecking the partition table on my live installation. But I basically have a 40Gb drive sitting there for the sole purpose of running grub for me!

I want to move grub to C so I can format B and use it for storage or as a test/dev space but would like to get some help on the process for safely moving grub before I attempt it again. I have looked at numerous guides but don't feel I quite have the understanding to attempt it again yet.

Anyone able to assist?

thanks in advance
Aaron

---

### Post by caljohnsmith on 2008-10-16
Hi Aaron, that should not be a problem, so how about first posting:
```
sudo fdisk -lu
```
Also, can you set your BIOS to boot the "C" drive first on start up? I assume that's not a problem, otherwise it won't do any good to move Grub to the C drive if you can't boot the C drive. :)

---

### Post by aaronp on 2008-10-17
```
Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x31e45af5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    24370604    12185271   83  Linux
/dev/sda2        24370605    78140159    26884777+   f  W95 Ext'd (LBA)
/dev/sda5        40965813    59569019     9301603+  83  Linux
/dev/sda6        24370731    28370789     2000029+  82  Linux swap / Solaris
/dev/sda7        28370853    40965749     6297448+  83  Linux
/dev/sda8        59569083    78140159     9285538+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000633be

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63    23438834    11719386   83  Linux
/dev/sdb2        23438835    91795409    34178287+  83  Linux
/dev/sdb3        91795410    95795594     2000092+  82  Linux swap / Solaris
/dev/sdb4        95795595   156280319    30242362+  83  Linux
```

thanks.

In answer to your question. When I first installed hardy on C I changed the boot order in the bios to boot from C and that's when I discovered that grub must be on the B disk because it didn't boot from C.

thanks
Aaron

---

### Post by issih on 2008-10-17
This is probably the easiest way to do what you want:

[https://help.ubuntu.com/community/GrubHowto#Command%20line](https://help.ubuntu.com/community/GrubHowto#Command%20line)

hope that helps

---

### Post by aaronp on 2008-10-17
thanks issih but i have done a fair bit of googling and i'm still just not quite sure i understand enough about it to risk doing it from a guide.
i followed a guide exactly (i thought!) last time and managed to stuff it up so not keen to repeat now that my installation is working well.

cheers
Aaron

---

### Post by issih on 2008-10-17
You have to do the steps listed under command line: i.e.

1 Boot your computer up with Ubuntu CD
2 Open a terminal window or switch to a tty.
3 Type "sudo grub" - the terminal prompt will change to "grub>"
4 Type "find /boot/grub/stage1" - You'll get a response like  "(hd0,1)". Use whatever your computer spits out for the following lines.
5 Type "root (hd0,1)", substituting in the value from step 4
6 Type "setup (hd0)", to install GRUB to MBR, substituting in the first number from the returned value of step 4 for the 0, i.e. use the bit before the comma.
7 Quit grub by typing "quit".
8 Reboot and remove the bootable CD. 

It can't be made any simpler than that really I'm afraid, unless you are willing to reinstall ubuntu

Hope that helps..shoot me a message if you get stuck

---

### Post by caljohnsmith on 2008-10-17
Aaronp, I think I see part of your problem; none of your partitions on your 80 GB sdb drive are flagged as bootable, so your BIOS may refuse to boot that HDD even if Grub is correctly installed. How about first following these steps from a terminal to correct it (applications > accessories > terminal):
```
sudo fdisk /dev/sdb
```
Press "a" to toggle the boot flag, then enter "1" for the partition, and "w" to write the changes to the HDD. Note that Grub can boot any of your valid linux partitions regardless of whether the boot flag is set on, so it is arbitrary which partition has the boot flag set (but only one partition on a HDD should have the boot flag set). 

The next step would be to ensure that Grub is correctly installed to the MBR (Master Boot Record) of the sdb drive, which you can do with the following steps from a terminal:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
Since you have multiple Ubuntu installations, you will most likely get multiple answers from the commands above; choose the one that is (hd1,X) where X is some number, for example (hd1,0), but use whatever it returns as follows:
```

grub> root (hd1,X)
grub> setup (hd1)
grub> quit
```
Then reboot, make sure your BIOS is set to boot the sdb drive, and let me know what happens or if you run into problems. :)

---

### Post by aaronp on 2008-10-18
thanks again caljohnsmith
Trying it now but got this message on the first command:

```

The number of cylinders for this disk is set to 9729.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

```

is this ok or something that needs attention before proceeding?

thanks again
Aaron

---

### Post by aaronp on 2008-10-18
OK, disregard my last post. I re-read the warning and made an executive decision to ignore it because it didn't relate to anything important.
I followed all of your instructions and when I boot from the sdb drive I get to grub but if I choose the first kernel version at the top of the list I get 
```
Error 15: File not found
```

Choosing the second kernel in the list (not recovery but next oldest kernel version) loads successfully. Pointing the bios back at the first hard drive allows me to boot into the top listed kernel as per normal.

thanks
AAron

---

### Post by caljohnsmith on 2008-10-18
Aaronp, that's great news you are getting the Grub menu; getting Ubuntu to boot now should not be a big deal if you don't have any other issues. :) Please post the output of the following so I can know which partition has your Grub:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
grub> quit
```

---

### Post by aaronp on 2008-10-18
thanks, here is the output:
```

grub> find /boot/grub/stage1
 (hd0,0)
 (hd1,0)

grub> find /grub/stage1

Error 15: File not found

grub> 

```

---

### Post by caljohnsmith on 2008-10-18
OK, reboot the sdb drive, and when you get the Grub menu select the first Ubuntu entry, press "e" to edit it, select the line that says "root (hdX,Y)" where X and Y are numbers, press "e" to edit it, change it to "root (hd0,0)", press return to save the change, then press "b" to boot. If that doesn't work, then also try (hd0,1) and (hd0,3); one of those should work if your Grub's menu.lst isn't too far off. Note that the above change is not permanent, so you'll need to modify your menu.lst to make it permanent.

So if it works, when you get into Ubuntu, just do:
```
gksudo gedit /boot/grub/menu.lst
```
And change the line that says "#groot=(hdX,Y)" to whichever (hdX,Y) worked to boot Ubuntu. Save, quit gedit, then run:
```
sudo update-grub
```
And you should be all set. Let me know how it goes or if you run into problems. :)

---

### Post by aaronp on 2008-10-18
thanks very much caljohnsmith.
before i try this can i just understand what we are doing here?
if we tell it to look for the installation in hd(0,X) are we saying look on drive sda? if so then that is an issue because the point of this exercise is so i can format and re-partition the sda drive and still access my installation on sdb via grub.

thanks again
Aaron

---

### Post by caljohnsmith on 2008-10-18
> **aaronp said:**
> thanks very much caljohnsmith.
before i try this can i just understand what we are doing here?
if we tell it to look for the installation in hd(0,X) are we saying look on drive sda? if so then that is an issue because the point of this exercise is so i can format and re-partition the sda drive and still access my installation on sdb via grub.

thanks again
Aaron
I know that Grub can be confusing, so let me try and explain a little more in depth from what I've learned about Grub: on start up, Grub sees the order of drives as the same as the BIOS boot order, because on start up Grub must use BIOS to access the drives. But the BIOS boot order has nothing to do with the device order in Linux's /dev directory, because Linux works through the kernel to access the drives; Linux's /dev directory is ordered by the type of device, so for HDDs they would be ordered by whether they are IDE, SATA, USB, and so on. 

So in practical terms, it means that if sdb is the first drive in the boot order (the drive you boot from on start up), Grub considers it the (hd0) drive on start up; therefore as long as you are sure the sdb drive is the one that is booting on start up, then you should use (hd0,X) to access Ubuntu on that drive. But when you are in Ubuntu, the sdb drive will be (hd1) when you run any Grub commands, because at that point Grub will use the same order of devices as in the /dev directory. Does that help clarify it some?

---

### Post by aaronp on 2008-10-18
got it, thanks for that. a simple explanation for something that seemed so complex. i appreciate your help.
I'll give your instructions a try and report back

thanks
Aaron

---

### Post by aaronp on 2008-10-18
perfect, it is working fine now.
now time to get partitioning! thanks alot for your help caljohnsmith.

one last thing. in my grub menu i also have a sub-list of kernels that exist on hda1 (all listed below). 
can i safely delete these entries out of my menu.lst file without corrupting it?

```

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (on /dev/hda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=5694d920-ac20-40fa-a286-2f0fe2465d6f ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode) (on /dev/hda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=5694d920-ac20-40fa-a286-2f0fe2465d6f ro single 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title		Ubuntu 8.04.1, kernel 2.6.24-18-generic (on /dev/hda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=5694d920-ac20-40fa-a286-2f0fe2465d6f ro quiet splash 
initrd		/boot/initrd.img-2.6.24-18-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title		Ubuntu 8.04.1, kernel 2.6.24-18-generic (recovery mode) (on /dev/hda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=5694d920-ac20-40fa-a286-2f0fe2465d6f ro single 
initrd		/boot/initrd.img-2.6.24-18-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (on /dev/hda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=5694d920-ac20-40fa-a286-2f0fe2465d6f ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


```

---

### Post by caljohnsmith on 2008-10-18
Yes, you can delete those extra kernel entries from your menu.lst, but the next time you get a kernel upgrade, they will most likely reappear again. The best way to keep them off your menu.lst is to change the stanza that has:
```
## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
[COLOR="Blue"]# howmany=1[/COLOR]
```
Just change "#howmany" line to however many kernels you want listed in your Grub menu, like "1" in the above example. Save the menu.lst and then run:
```
sudo update-grub
```
And you should only have 1 kernel listed in your Grub menu.

---

### Post by aaronp on 2008-10-18
thanks very much! have a good day
cheers
Aaron

---

### Post by caljohnsmith on 2008-10-19
Glad it's all working now, and you're certainly welcome. :)

---

