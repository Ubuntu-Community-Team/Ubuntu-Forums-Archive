---
title: "Computer rebooting early during installation."
date: 2005-09-03
forum: Installation &amp; Upgrades
---

### Post by ZombieCat on 2005-09-03
OK, I haven't been able to find any problems that quite match mine, so I figure I'd better post something ...

I'm trying to install Ubuntu onto a FAT32 partition. I plan to use this computer as a dual-boot, with Windows XP being the other OS. I'm using a burned downloaded disc to install Ubuntu, which I know isn't corrupted or anything. I can get as far as the introductory splash screen, but my problem is that my computer will reboot whenever the Linux kernel attempts to load. It's done the exact same thing with an Ubuntu LiveCD and an old Mandrake CD, always rebooting when the kernel attempts to boot. And all three of those will work on a different PC, so I know it's not the discs themselves.

I've gone through the forums and tried just about everything I can think of ... tried all the boot parameters, made sure the CD drive was ahead of the hard drive in boot order, made sure the processor wasn't overheating, etcetera.

I'm running a Compaq Presario SR1210NX with 256 MB of RAM and a 2.66 GHz processor. My BIOS is a Phoenix AwardBIOS, version 6.00, and my CD drive is ... ... well, dang. I don't even know *what* it is. it's a combo DVD/CD-RW drive, but it's only showing up as "generic". I'm guessing that MIGHT be my problem, but like I said, it was able to burn the disc perfectly, and it's never given me any problems before.

If anyone has any ideas or suggestions, they'd be vastly appreciated.

---

### Post by ZombieCat on 2005-09-03
I figured that since the problem was probably linked to booting the kernel from the CD, I'd take some initiative and try the alternate method of booting the kernel from the hard drive, then following up the installation on the CD. 

... Except now, when I click Install Ubuntu during startup, I get an error message that says:

"Windows could not start because the following file is either missing or corrupt:
<Windows root>\system32\hal.dll"

Okay, what? *Windows* could not start? Am I missing something really obvious? I copied the contents of the CD, appended boot.ini, got grldr and made sure menu.1st pointed to actual directories ... so why is Windows trying to load? Is it just trying to fetch the kernel? A quick search has told me that this error often occurs from an incorrect boot.ini. Well, jeez. I'm stuck either way.

Does anyone have any insight into this? Having to sit through Windows' painful startup after every failed attempt is becoming frustrating.

---

### Post by yorick on 2005-09-05
Ok, I'm a newbie myself, but I'd like to try and help.
I don't exactly understand the specifics of your problem. Do you want to install Ubuntu on a FAT32 partition? Doesn't it have to be ext3 or ReiserFS or some other Linux-type partition? 
Are you trying to install Ubuntu on the same partition with Windows? How many partitons do you want to have in the end and what type should they be?

---

### Post by ZombieCat on 2005-09-05
As far as I'm aware, the file format of the partition to be installed to can be anything. Linux just reformats it during the install. The partition I'm planning on installing to is actually a recovery partition, but these things have never worked for me, and I make CD backups of my work anyway, so I might as well put it to good use, eh?

... Uh, anyway, the partition in question doesn't have Windows on it, if that's what you're asking. It's the only one I plan on using, and I assume Ubuntu will split it into several smaller pieces for swap files and whatnot.

But all of that's a moot point, since I can't even get to the installation screen. Choosing/resizing a partition would be a lot farther down the road. I'm still working on trying to get the kernel booted without my computer trying to kill itself.

I guess I should also mention that I've tried running the Rescue CD mentioned in the dual boot section of the manual. It also failed, but much farther down the line, when the individual systems were being loaded. I've also been able to run Damn Small Linux Embedded from within Windows, so I suppose it's a problem with my computer's boot process. Or the BIOS.

I don't know. Sorry if I'm incoherent. It's way too early in the morning to be typing.

---

