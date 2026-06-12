---
title: "Grub Error"
date: 2006-10-19
forum: Installation &amp; Upgrades
---

### Post by sohaibma on 2006-10-19
Firstly, i am a newbie.
Now, yesterday i intalled ubuntu LTS 6.06, in the second partition on my HDD (first one contains winxp sp2). when i rebooted the system it showed the following error: 
Loading grub
Error 21.

and nothing then.

can someone please help me out here. How can i fix this problem.

---

### Post by bulldog on 2006-10-19
Yes well,error 21 means:
21 : Selected disk does not exist
    This error is returned if the device part of a device- or full file name refers to a disk or BIOS device that is not present or not recognized by the BIOS in the system.

Can you put the output of```
sudo fdisk -l
``` l as in like

---

### Post by h4rdwire on 2006-10-19
isn't this redundant? thought i replied to this or was it a different one.

Check layer one....Physical problems/hardware

---

### Post by sohaibma on 2006-10-20
since i am a new, i have no idea what sudo fdisk -I means. and how to execute it.
please explain

PS how can i use winxp despite this error.

---

### Post by Herman on 2006-10-20
If you just want to boot Windows XP for now until you get Grub fixed, [GAG Page]("http://users.bigpond.net.au/hermanzone/p12.htm").....or....[Super Grub Disk Page ]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html"),  one of those links should help you. You can also boot Windows XP with a Windows XP boot floppy disk, you can make one of those yourself, [Click Here]("http://support.microsoft.com/kb/305595/EN-US/").

You might be able to figure out Grub by reading this link, [GRUB Page.]("http://users.bigpond.net.au/hermanzone/p15.htm")
That will help you to understand the help you will get.

The command 'sudo fdisk -lu' is a command yopu can enter in a terminal (Applications ->Accessories -> Terminal) for obtaining information about your hard disk and partitioning arrangement. This information is very useful to someone who might want to help you with fixing you Grub bootloader problem. ```
sudo fdisk -lu
``` (That's an 'l' (for 'list' too, not an I). :D
 Regards, Herman :D

---

### Post by towsonu2003 on 2006-10-20
> **sohaibma said:**
> since i am a new, i have no idea what sudo fdisk -I means. and how to execute it.
please explain

PS how can i use winxp despite this error.

Sorry that I'm just linking to documentation here, but it usually is a little easier and faster to use documentation to recover from stuff like this. 

See this one to try to recover your grub installation [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

And if that doesn't work, see this one to get your windows boot loader back: [http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true)

The second link needs you to have a Windows CD and use the recovery console. I hear you say "what's that?"; see this link: [http://support.microsoft.com/kb/314058](http://support.microsoft.com/kb/314058)

Also, if you indicate what kind of a system you have (type of drives, model of computer etc) someone might be able to help. 

The ```
sudo fdisk -l
``` should be executed from under Ubuntu, which you cannot boot into now. you can use the live CD to exeute that command as well. it will **l**ist (hence **-l**) all the partitions in your hard drive(s). If you manage to report us the output of *sudo fdisk -l*, please let us now of where your Windows & your Ubuntu installations are located (which partition). 

Let me give you an example quickly. Below, you will see me giving the command and getting the output:
```

towsonu2003@localhost:~$ sudo fdisk -l
Password:

Disk /dev/hda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1824    14651248+   7  HPFS/NTFS
/dev/hda2            1825       12161    83031952+   5  Extended
/dev/hda5            1825        2067     1951866    b  W95 FAT32
/dev/hda6            2068        3283     9767488+  83  Linux
/dev/hda7            3284        3405      979933+  82  Linux swap / Solaris
/dev/hda8            3406       10700    58597056   83  Linux
/dev/hda9           10701       11465     6144831   83  Linux
/dev/hda10          11466       12161     5590588+  83  Linux

```
As you see, I have 8 partitions. hda1 (first partition I have) is where my windows is installed. hda6 (4th partition I created) has Ubuntu, hda9 and hda10 has 2 other distros. 

When you use the LiveCD (also called the Desktop CD), try to access your Linux partition, and attach this file here: /boot/grub/menu.lst

this file should be inside one of the mounted partitions, probably under /media

so the resulting path to that file is **/media/***????***/boot/grub/menu.lst**
to find out what *????* is, check the folders under **/media**

This link has nice information about how to access your partitions and so on: [https://help.ubuntu.com/community/Mount?highlight=%28mount%29](https://help.ubuntu.com/community/Mount?highlight=%28mount%29) 
it will be useful to you in case the Live CD doesn't automatically mount your Linux partition(s) (i.e. if you don't see any folders under /media, or on your desktop perhaps). 

I hope this is helpful. Also, I would appreciate anyone around here to clarify what I'm saying, as english isn't my first language and what I wrote may not be as clear as I hink it is. thanks :)

---

