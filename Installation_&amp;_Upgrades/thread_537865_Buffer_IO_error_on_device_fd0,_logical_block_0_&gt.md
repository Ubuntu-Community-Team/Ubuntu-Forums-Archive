---
title: "Buffer I/O error on device fd0, logical block 0 &gt;&gt;&gt;Solved"
date: 2007-08-29
forum: Installation &amp; Upgrades
---

### Post by 1clint on 2007-08-29
This is the error I got on my Dell 4000 [xxxx.xxxxx] Buffer I/O error on device fd0, logical block 0

Problem- Computer reaches Ubuntu install page, selected graphical install on screen runs through  about 5 minutes and hangs up with th Buffer I/O error on device fd0, logical block 0 error. Now I dont have a floppy drive and it is disabled in the bios. The computer had Ubuntu loaded before not by me, so I know some how it did work. So I got the factory floppy diskette, enabled the bios boot sequence to look for a diskette drive etc..etc. Still same problem, then I noticed on the laptop it had 128 MB of RAM, 700 MHZ processor. Way old right, well then I reviewed memory requirements for install. BAM...problem solved.



Solution -on these old laptops there is a limited memory available. On most of the installations they require utilizing at least 256 MB of dedicated RAM meaning if you have shared graphics you fall below this if this is the system minimum. So in short there are some fixes if you have this problem
-Down Load this version .... **ubuntu-7.04-alternate-i386**
-Try installing with  a **CD ROM** not a CD-RW/DVD/CD ROM drive
-Utilize Text Mode Installlation

Closing- I have read about this problem extensively, this is a very common load problem, I hope this helps some of you out there and the forum helped greatly. Thanks

---

### Post by lenzpa on 2007-08-30
I have had exactly the same problem on an old DELL C810. On the third attempt, I left the error message on the screen for about 10min (coffee time) and Ubuntu automatically resumed the installation...

---

### Post by jogeer on 2007-09-23
I found this page that might be usefull: 

[https://answers.launchpad.net/ubuntu/+question/7697](https://answers.launchpad.net/ubuntu/+question/7697)

It apears the system is looking for a drive that isn't there. 

Cheers.

---

### Post by BLTicklemonster on 2007-11-22
Allllllrighty then, I'm trying to install on an old Dell, and I get the same message. I'm just in the boot from live CD part and I'm getting it already. But, I hear the machine doing stuff and see it keeps trying, so maybe it's okay after all.

I came here looking to see what it meant after trying like 4 times on gutsy, then trying 3 times with feisty. Okay, it' s moving along now. 

Whee.

*Edit:

Okay, it's installed!!! Old dell laptop with a 750 meg celeron, 256 megs ram, running feisty. Installing icewm to get a bit more speed out of it right now.

Muahahahaha, portable Ubuntu!!!

---

### Post by bluec99 on 2007-11-29
I had some fun with this using mythbuntu on dell 8100.  It has dvd/cdrom in the side and cdburner in the front bay.

booting from mythbuntu in the side dvd/cdrom always failed video with big gray blocks on the screen.  booting from front bay cdburner worked.  no idea why that affects video.  100% reproducible though.

I saw Buffer I/O error on device FD0, Logical Block 0 on boot but wasn't concerned because there is no floopy drive.  However, I noticed the machine periodically hanging for a couple seconds.  reviewing /var/log/messages this is the only thing close to an error I could find.  so:
sudo rmmod floppy

now seems to hum along just fine with no hangs.  I'm looking for how to prevent floppy from loading and found this:
/etc/modprobe.d$ grep floppy /etc/modprobe.d/*
/etc/modprobe.d/isapnp:alias pnp:dPNP0700 floppy

I'm hoping comment this out will prevent floppy module from loading.  `man modprobe.d` supports this theory.  Anyone know for sure?
update: didn't work . backing out this change and trying blacklist of floppy module:
[http://www.cyberciti.biz/tips/avoid-linux-kernel-module-driver-autoloading.html](http://www.cyberciti.biz/tips/avoid-linux-kernel-module-driver-autoloading.html)

---

