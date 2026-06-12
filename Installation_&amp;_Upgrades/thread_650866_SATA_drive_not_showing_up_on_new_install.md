---
title: "SATA drive not showing up on new install?"
date: 2007-12-26
forum: Installation &amp; Upgrades
---

### Post by transporter_ii on 2007-12-26
I just created a dual boot Ubuntu 6.06 LTS/Windows Vista system on a new Everex Impact GC3502. I detailed how I did my install here:

[http://ubuntuforums.org/showthread.php?t=649403](http://ubuntuforums.org/showthread.php?t=649403)

I'm happy with how everything turned out, but I have one issue that bothers me. I have one SATA and two IDE drives in this computer. The SATA drive, where Vista was already installed, wasn't an option during the install from the Live CD, and the SATA drive does not show up in Ubuntu in the file browser or when I go to System\Administration\disks. Both IDE disks showed up right off the bat.

I checked BIOS of the system, and the mode of the SATA Controller is "IDE." I also belive it is the channel 2 master, but I could be wrong about that. The only place where I know the SATA drive exists, is in GRUB, where I see it as hd1 and hd3 (and hd3 is where the main Windows partition is, because it will boot from it, and hd1 is some kind of Windows Vista recovery partition, I believe).

As stated, the system is working exactly as I want it to, but it would be nice if someone could point me in the right direction to solve this, because, who knows, I might want to access that SATA drive from Linux some day...or do an install for someone else and this turns out to be an issue.

Note that if I do a "sudo fdisk -l," I get 2 drives back:

Disk /dev/hdc: 160.0 GB,
Disk /dev/hdd: 160.0 GB, 

Both of which are the IDE drives that have showed up all along.


Transporter_ii

---

### Post by portrower8 on 2007-12-27
I am having the same problem!


My windows xp is on SATA RAID drive... and I installed ubuntu on IDE drive..

but now I can't access the SATA drive!

how do I fix?  I can't boot from windows either! it doesn't prompt me. it goes straight to ubuntu each time!!

---

### Post by transporter_ii on 2007-12-27
Ok, at first I was thinking this was no big deal, considering I wanted a dual boot system and I actuall have one.

However, I actually think I have stumbled on either a bug or a driver issue with Ubuntu (6.06 LTS).

When I finished my first install, in BIOS, my SATA controller (?) was set to IDE. On startup, GRUB showed the following disks:

hd0 hd1 hd2 hd3

I thought that was a little odd, because I only have 3 hard drives in the box (One SATA and two IDE). But what do I know?

Doing a little research, I found someone doing a review of an Everex system. They said they had to, in BIOS, set the SATA driver to RAID to get the SATA drive to show up in Ubuntu.

Well, I give it a try. Set on RAID in BIOS, I get a strange message before GRUB on bootup, but my SATA drive shows up in Ubuntu. The only problem now is my Windows Vista (on SATA) starts to boot, but then the system reboots.

Giving the reboot problem, I go back into BIOS and change the SATA RAID setting back to IDE. Now when I reboot and go into grub, I have the following:

hd0, hd1, hd2

After editing my Grub Windows Vista menu.lst item to reflect the change, Vista boots right up and the system reboot problem is gone. However, I can no longer see the SATA drive in Ubuntu.

Now I'm back to where I started, I have a working Ununtu/Windows Vista dual boot system, but for some reason, Linux cannot see the SATA drive.

Now I do know a way to make Ubuntu see the SATA drive...but then VISTA quits booting (Now I would say YEAH!!!, but it does kind of defeat the purpose of a dual boot system, now doesn't it?)

Transporter_ii

---

### Post by transporter_ii on 2007-12-29
Solved the problem. I just downloaded the live CD in the last couple of months, but I downloaded the 6.06 LTS version. Even totally updated, it does not have support for the via chipset.

The Everex GC3502 uses this chipset:

Northbridge: VIA CN896
Southbridge: VIA VT8237A 

I downloaded a 7.10 Live CD and the SATA drive shows up just fine as a drive available to install to. I have not installed it yet, but I'm sure this is the solution.

Transporter_ii

---

