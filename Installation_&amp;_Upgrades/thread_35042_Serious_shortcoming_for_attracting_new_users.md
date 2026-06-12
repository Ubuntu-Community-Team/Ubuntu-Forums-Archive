---
title: "Serious shortcoming for attracting new users"
date: 2005-05-17
forum: Installation &amp; Upgrades
---

### Post by rvergara on 2005-05-17
I have been a Linux user since I installed RH 6.0 about 5 years ago. It was very traumatic since I was a total newbie and try to do a dual boot with my W98 PC, the installation destroy the MBR content and I had to rebuild it. 

Installation those days were not easy but I was determined so I completed it and I have been using RH since then. RH9 installation was a breeze. Due to the change on RH support policies I have decided to migrate from RH to something else, I got very impressed with the Ubuntu Live CD and all the community environment so I will probably migrate from RH9 in the next couple on months (no easy migration path for this). However I got very concern on Ubuntu ability to properly perform a dual boot installation because GRUB seems to be causing problems with the MBR.

Ubuntu will not attract windows users unless they are able to test drive the installation with a dual boot. So dual boot installations have to work, perfectly, every time.

This is a serious shortcoming for Ubuntu that I am almost sure will be addressed very rapidly just by seeing how the community moves swiftly in resolving issues. IF RH resolved this issue 5 years ago I do not see why Ubuntu can not do it rapidly.

Regards

Ramiro

---

### Post by dave9191 on 2005-05-17
Ive never had a prob with Ubuntu / Grub / Dual booting. I just make sure that there is some space for ubuntu to install and let it do its own thing (well i tweak the partion tables, but thats not essential). Ubuntu installer always tells me that Windows has been found and asks me if there are any other OS it missed. It then configures Grub and saves me a lot of hassel. I've installed ubuntu onto serveral different machines and not a single prob. So I think that its does a good job. But as always, nothing is perfect 100% of the time.

---

### Post by tomchuk on 2005-05-17
Huh? I've installed Ubuntu in dozens of dual boot environments, and grub has been setup flawlessly every time. Can you be more specific about your problems than "GRUB seems to be causing problems with the MBR"?

IIRC, RH has had issues with dual boot installs as recently as FC2 - the installer incorrectly modified the drive geometry in the partition table, leading to an unbootable Windows install.

---

### Post by scaramonga on 2005-05-17
Dual boot works flawless here!..........bit of tweaking to Grub......but otherwise fine  O:) 

Just wish my sound would work and it would be damn perfect!  [-o<

---

### Post by zxc on 2005-05-17
No he's right. I personally haven't had any problems but I remember reading loadsa cases of problems. Check out DualBootHOWTO on the Wiki for an example of a person who has experienced problems.

---

### Post by clb137 on 2005-05-17
NOt sure what you guys are doing, but DUAL boot works fine every time and all the time,  need to be a little more specific with your problem/errors

---

### Post by tread on 2005-05-17
I didn't want to start a thread just to get this question answered, and it does seem to fit this thread.

I have had a partition before I setup Ubuntu. Mandrake offers a partition resize option during install. Does Ubuntu give the same option? I don't remember seeing one .. so if I have a machine that has say a 40 gb harddrive with windows on a single partition, does the Ubuntu install cd have parted to resize the partition?

---

### Post by DarkTrancer on 2005-05-17
The installer might be perfect for the people it works for and who have an installed ubuntu system working,but _there_ are other people who are having problems,and not just n00bs either.
I have been using linux since the rh 6.2 days,not constantly i`d admit but enough to try out any new distros i come across.My last install of ubuntu (4.10) worked great even on my hardware,however no matter how many times i try to install 5.04 it just doesn`t want to play with my config.I have a amd64/gigabyte k8nsnxp,2x300gig maxtor 10satas on raid0,2x200gig maxtor9satas on raid0,2x200gig maxtor 9`s on ata133,and wd 80gig for dedicated linux.
During install,if i choose grub it will wreck the mbr and give a error 17,if i choose lilo it too fails with error 1. Even trying to install grub or lilo to only the linux drive hdd5 in my case fails.
The live cd/dvd works with perfection however install does not.

---

### Post by Bob D. on 2005-05-17
> IIRC, RH has had issues with dual boot installs as recently as FC2 - the installer incorrectly modified the drive geometry in the partition table, leading to an unbootable Windows install.
This was actually a kernel issue....affected many other distos (Suse, etc.) other than RH/Fedora.

Bob

---

### Post by az on 2005-05-17
[QUOTE=tread]I didn't want to start a thread just to get this question answered, and it does seem to fit this thread.

I have had a partition before I setup Ubuntu. Mandrake offers a partition resize option during install. Does Ubuntu give the same option? I don't remember seeing one .. so if I have a machine that has say a 40 gb harddrive with windows on a single partition, does the Ubuntu install cd have parted to resize the partition?[/QUOTE]


The installer can resize linux and windows partions.  Just pick the partition you want and make it's size smaller and some free space will pop up.

DarkTrancer:  Bug report?

rvergara:  Again, a bug report would better serve the community.  Please file one.   What you describe is _not_ supposed to happen.

---

