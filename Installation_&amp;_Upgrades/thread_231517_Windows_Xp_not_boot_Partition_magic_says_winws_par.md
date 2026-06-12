---
title: "Windows Xp not boot Partition magic says winws partiion Linux Ext2"
date: 2006-08-07
forum: Installation &amp; Upgrades
---

### Post by ewanmac on 2006-08-07
I have installed Ubuntu dapper drake onto my dell 5160 laptop.

I wanted to keep windows Xp and dual boot so I used Gparted to create the partion for ubuntu and the partion for the swap file.

Ubuntu boots fine and I can access the windows files.

When I try to boot XP I get the message:
A file is missing or corrupt <windows root>\system32\hal.dll  Please re-install a copy of the above file.

I have followed the advice given elsewhere in the forum (Repairing Windows XP in Eight Commands)and got as far as BOOTCFG /REBUILD. Windows tells me there is an error and it can not complete.

CHKDSK does not find any problems. [http://ubuntuforums.org/images/smilies/eusa_wall.gif](http://ubuntuforums.org/images/smilies/eusa_wall.gif)
](*,)

Gparted says the windows xp volume is NTFS which it was before I started but Partition Magic 8 says the volume is Linux ext2 and Fdisk says it is a Linux File system.

What can I do to repair the XP boot so I can dual boot?

Many thanks in advance, this is my first foray into the world Linux.[http://ubuntuforums.org/images/smilies/icon_smile.gif](http://ubuntuforums.org/images/smilies/icon_smile.gif)
:)

---

### Post by gn2 on 2006-08-07
Have you removed the drive and connected it to another computer?

Surely Partition Magic should be able to convert Windows partition to NTFS?

Or just delete it to make more space.....

Obviously, back files up to another drive or removable media first.....

---

### Post by ewanmac on 2006-08-08
Thanks for the reply I appreciate it.

It seems the failed initial install damaged the files system in someway.

I temporarily uninstalled Unbuntu and just left windows.

I kept going round in circles but with Partion Magic not wanting to touch the drive and various products including windows reporting the MBR was an unusual files syetem (without Grub) I just cut my losses and reformated the lot.

---

### Post by gn2 on 2006-08-08
Did you get a dual-boot set up?

I have had difficulties with that myself on my main PC.

I am trying out Ubuntu on an old laptop to get used to it, once I'm more confident I'll have a go at the main PC again.
Perhaps add a second hard drive for Ubuntu, (installing with the windows hard drive unplugged) and use the bios boot device selector...

Stick with Ubuntu, I'm only keeping Windows XP because it's already paid for. When support is turned off I won't be buying Vista...

As far as I can see, Linux is now a viable alternative for the average user who isn't an uber-geek

---

