---
title: "installation death"
date: 2007-12-19
forum: Installation &amp; Upgrades
---

### Post by AuToFiRE on 2007-12-19
Well I loved 7.04 so i upgraded to 7.10 and it didnt work out too well, i lost flash and java so i formatted and started over with a  fresh 7.10, it worked ok but there were several issues i was unable to fix, so i decided to downgrade to 32-bit 7.10 but.. it would install but it wouldnt boot complaining about no boot options. Then i reinstalled 64-bit 7.10 and now i cant install certain programs because of errors. could it be my hard drive is failing? it would explain why windows randomly stopped working and wouldnt reinstall in the first place when i decided to switch to Linux. Is there any program i can run right now on sda1 to see if the hard drive is failing?

---

### Post by perlluver on 2007-12-19
Boot into single user mode from Grub, and run fsck on it.  That will check the hard drive for errors, and if it is going bad it mentions bad blocks.

---

### Post by Herman on 2007-12-19
Yeah, and also you can try running the badblocks command and see if you get any output from that too.
Here's a link about it: [Bad Blocks]("http://www.brunolinux.com/04-The_File_System/Bad_Blocks.html").

It will take a while to run and if you don't get any feedback from it your partition has passed. 

Also, you can install [smartmontools]("http://smartmontools.sourceforge.net/") and smart-notifier through Synaptic Package Manager and probably apt-get.

---

### Post by AuToFiRE on 2007-12-23
Just an update for you guys, its not bad blocks, it looks like its repeatedly bad installs, i will download a fresh copy and burn it again, maybe that will solve the problems

---

### Post by Herman on 2007-12-23
:) Okay, that can happen to anyone, even if we do everything we should, like [md5sum our dowloaded .isos]("http://www.users.bigpond.net.au/hermanzone/p17.htm#Why_integrity_check_your_downloaded_.iso"), and check the CD for defects before we begin the install, an installation can still be problematic due to a dirty optical drive lens or some other small annoyance like that. I hosed my wife's computer's partition table one time an it turned out to have been caused by a dirty CD-ROM drive lens interrupting the partitioning. Neither compressed air or a DVD cleaning disk were effective at all to fix it.  I had to take the CD/DVD drive out and dismantle it to clean the lens with a  cotton bud (or 'QTip') and some methylated spirits (also called 'denatured alchohol', in some countries).  
 It has worked perfectly ever since (thank goodness), and I had the newer version of Ubuntu installed by the time she got home. :)

I got interested in smartmontools myself since my earlier post in this thread and made a small how-to about that in my Knoppix Page,  [Check On Your Hard Disks With Smartmontools]("http://users.bigpond.net.au/hermanzone/p20.html#Check_On_Your_Hard_Disks_With"). The only difference with Ubuntu is we have to install smartmontools first, but using the program is the same. (Just in case there's anyone out there who wants to keep an eye on their hard disks). 

Good luck with installing this time, AuToFiRE, I hope it goes better for you from now on,
Regards, Herman :)

---

### Post by AuToFiRE on 2007-12-23
Yeah, its just really weird though, several installs all screwed up one after another, different architectures and different discs . it was the main reason i switched to Linux, windows didnt recognize my hard drive anymore, even the install cd didnt, but now im on Linux and love it but when your hard drive does that it scares me

---

