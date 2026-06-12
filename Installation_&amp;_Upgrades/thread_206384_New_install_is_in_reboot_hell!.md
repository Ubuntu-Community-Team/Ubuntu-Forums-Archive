---
title: "New install is in reboot hell!"
date: 2006-06-30
forum: Installation &amp; Upgrades
---

### Post by seebarn on 2006-06-30
I just installed Ubuntu 6.06 (server LAMP stack) onto a system that already has Debian (2.6.14 kernel) and I'm in a bit of a bind ...

The system is Linux-only, with Debian's root on /dev/hda1 and Ubuntu's root on /dev/hda3.  Install went seamlessly, and the grub install properly saw and configured for Debian.  Grub is installed to the MBR on /dev/hda.  After the install, I removed my CDROM as directed and let it reboot.  Which it now does infinitely if left to itself!

Grub displays its commands, and right after the "boot" command the system reboots, restarts grub, rinse, lather, repeat.

If I override the default and tell it to boot the old Debian system, that works fine.  Also, if I tell it to boot the Ubuntu memory test, that works fine, which leads me to believe it's at least got the drive geometry right and is able to access /dev/hda3 fine (otherwise the mem test should fail in the same manner as the Ubuntu kernel).

The reboot occurs instantly after the grub "boot" command - there's no "Uncompressing Linux ..." message, etc.  The kernel version is vmlinuz-2.6.15-23-server.  

Grub menu config is as follows:

title       Ubuntu, kernel 2.6.15-23-server
root       (hd0,2)
kernel     /boot/vmlinuz-2.6.15-23-server root=/dev/hda3 ro acpi=off
initrd      /boot/initrd.imb-2.6.15-23-server
safedefault
boot


Any tips or pointers would be appreciated!

---

### Post by seebarn on 2006-07-02
No ideas, anyone?

---

### Post by beausimon on 2006-07-02
You said you boot into memory test ok. If you boot manually into ubuntu server, do you have this problem?

---

### Post by seebarn on 2006-07-03
Yes, if I manually select Ubuntu from the grub menu (either the normal version or single-user recovery version)  the problem occurs.  The memory test is at least telling me that the partition itself is OK, and likely the grub menus as well (not a lot of room for mistakes in there anyway), so I suspect it's something with the kernel itself but I'm not sure where to begin looking there.

---

### Post by Shadowfire on 2006-07-04
I have the same problem.  I have tried several reloads and different componets - such as video card. Still no resolve.  Anyone have any idea what is the cause of reboot?

---

### Post by seebarn on 2006-07-04
Shadowfire, are you seeing the reboot occur after grub starts booting linux but before the "Uncompressing Linux" message appears?  And are you able to run the memory test (which also helps verify that the partition and grub are working)?

---

### Post by confused57 on 2006-07-04
I can't explain what's causing problems with the Dapper server CD, but I tried to install it three times on an old computer(different iso downloads), 500MHz AMD K6-2, 256 mb ram...same result, system just continuously reboots.
Tried installing on my Dell Dimension 4550, 2.0 GHz, 512 ram...installed and ran perfectly.   The only way I could install a server to my old computer was to install from the Dapper Alternate CD.   I've seen quite a few posters with this problem.

---

### Post by Shadowfire on 2006-07-04
[QUOTE=seebarn]Shadowfire, are you seeing the reboot occur after grub starts booting linux but before the "Uncompressing Linux" message appears?  And are you able to run the memory test (which also helps verify that the partition and grub are working)?[/QUOTE]

just as you said, the reboot occurs instantly after the grub "boot" command.   

Shown below:

Booting "Ubuntu, kernel 2.6.15-23-server'

root (hd0,0)
 Filesystem type is ext2fs, patition type 0x83
kernel /vmlinuz-2.6.15-23-server root=/dev/hda3 ro quiet splash
   [Linux bzImage, setup=0x1c00, size=0x16b75f]
initrd /initrd.img-2.6.15-23-server
   [Linux-initrd @ 0xb940000, 0x69f742 bytes]
savedefault
boot

At this point the Ubuntu bootup process reboots and tries to boot ubuntu again... and again.. and again... and so on

So that is where I get to..  Oh and as you can tell I am loading the server version on a server of mine.

---

### Post by Shadowfire on 2006-07-04
[QUOTE=confused57]I can't explain what's causing problems with the Dapper server CD, but I tried to install it three times on an old computer(different iso downloads), 500MHz AMD K6-2, 256 mb ram...same result, system just continuously reboots.
Tried installing on my Dell Dimension 4550, 2.0 GHz, 512 ram...installed and ran perfectly.   The only way I could install a server to my old computer was to install from the Dapper Alternate CD.   I've seen quite a few posters with this problem.[/QUOTE]


That must be it then... something in the older componets.  I am running a AMD K6-3 450MHZ  with 192MB ram, (2) 20GB HD, CDRW, and DVD-RAM.

Infact it is still running right behind me - rebooting... beep... beep..  lol

I am going to try a daul boot install on my desktop I am using right now.  Hope it works out.

wish me luck! :-s

---

### Post by confused57 on 2006-07-04
[QUOTE=Shadowfire]That must be it then... something in the older componets.  I am running a AMD K6-3 450MHZ  with 192MB ram, (2) 20GB HD, CDRW, and DVD-RAM.

Infact it is still running right behind me - rebooting... beep... beep..  lol

I am going to try a daul boot install on my desktop I am using right now.  Hope it works out.

wish me luck! :-s[/QUOTE]

For whatever reason that was causing it, I came to the same conclusion about older components and the server CD.  Good luck...it "should" work on a faster computer, did for me.

---

### Post by seebarn on 2006-07-05
I'll try re-installing using the Alternate CD this evening and post my results here.  In my case we're definitely talking about older hardware - it's an ancient Gateway machine from the Pentium 200Mhz era, but its served very well the last few years as a file server & web development testing server.  ;-)

---

### Post by xchrisday on 2006-07-06
I'm having similar problems with an old daewoo machine with a k6-2 450 running at 400mhz due to motherboard restrictions, a few other threads suggest using the alt install cd as a fix which is what im doing now.

---

### Post by Shadowfire on 2006-07-06
[QUOTE=seebarn]I'll try re-installing using the Alternate CD this evening and post my results here.  In my case we're definitely talking about older hardware - it's an ancient Gateway machine from the Pentium 200Mhz era, but its served very well the last few years as a file server & web development testing server.  ;-)[/QUOTE]

Guys apparently either the older motherboard (no apci) or AMD K6-3 450 were the problem I believe.  I just loaded it on a Athlon XP 2000+ computer and Intel Celeron 1.6Ghz computer and both installs went through without a hitch.

Just thought I would share.  As much as I love using older parts for servers because they work fine for home use, I will be bumping up the CPU to at least 1GHz.  It seems I should be safe with that range of CPU and motherboard.

---

### Post by seebarn on 2006-07-08
I had tried the various ACPI options both in BIOS, install and kernel bootup with no success ... but the alternate install CD did the trick flawlessly, the system is booting as I type this (OK, that means I'm not absolutely sure it worked yet, but it's a lot further along than it was before ;-)

*Following this post, the system did finish booting and it's working great.  I'm off in the land of installing and configuring software now.  :-) *

I didn't do anything dramatically different when using the alternate CD for the install, and it looks like the same kernel release as the server CD (haven't done a binary compare, but the version numbers are the same).  Does anyone know what would be so different between the two CDs that one would work when the other failed?  Maybe there's something that could be backported from the alternate CD to the main CD to make it more install-tolerant.

---

### Post by xchrisday on 2006-07-09
The fix, which has worked for me, is to install the 386 kernel :D

use the install cd to initiate a rescue.

Get through to the shell

use the command: apt-get install linux-386

And enjoy!

edit: for spelling

---

### Post by ihavenoideax2 on 2007-04-25
This worked just perfect on my AMD k6-2 350 with 256 mem. Now setting it up as a ftp server.

---

### Post by adamantivm on 2008-05-10
Thank you very much! I was stuck for two weeks with this endless boot cycle on grub on an old Pentum-S 133MHz. Adding a 486 kernel (I was installing Debian, not Ubuntu, sorry!) got me out of that situation.

---

