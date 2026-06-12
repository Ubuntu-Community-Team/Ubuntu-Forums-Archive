---
title: "Partition Help"
date: 2004-11-03
forum: Installation &amp; Upgrades
---

### Post by eldrich_rebello on 2004-11-03
Hi all,
I heard that the Ubuntu installer is similar to that of debian.I'm a novice at disk partitioning and could use some help with that part of the install.My cd's are still on thir way here and so I got some time on hand to sort out these things first.
I have windows XP pro on C ,a blank D,mp3's on E and blank G,cd rom is F;i have one physical 40 gb HDD.how do i go about telling ububtu that i want it installed in addition to windows.I'll probably install suse 9.1 before ububtu as YAST is a nice installer ,or so i heard.I have pertition magic 6 currently.  :neutral: i think i'll be using the suse boot loader as i've heard that it detects XP and adds it to the boot menu.How exactly do i get Ububtu to add itself to this boot menu?
Any help appreciated

Eldrich
P4 2.5GHZ
512 RAm
40 GB HDD
INTEL EXTREME GRAPHICS 1

---

### Post by Dennis_k on 2004-11-03
Ubuntu installs GRUB in the main mbr of your disk.
It detects the operating systems on your disk(s) and ads them, so when you boot you will get a list of SO systems that you can boot

---

### Post by az on 2004-11-03
Suse 9.1 would never install for me.  Forget it.  You won't need it.  Ubuntu will do all that stuff for you.  It will scan all the disks for other operations systems and add them to the grub menu, as it installs grub to your boot record.

Use your partition magic to shrink your 40 gig windows partition down to whatever you want.  The tell the ubuntu installer to do manual partitioning.  Then use the free space.  Make a swap partition too,  Say 600Megs.  Easy.

---

### Post by eldrich_rebello on 2004-11-03
Thanks,both of you,appreciate your time... :smile: 
does the ubuntu installer provide for creating a swap partition?also ,can i do the same from partition magic?and...if i resize my windows partition will i loase my data?
i'm considering burning a backup to a cd (a couple) and then doing a clean install of ubuntu..but will my windows programs run on ubuntu or suse?any program other than wine?absolutely hate windows and microsoft....please  tell me if i MSN messenger works in linux..or is there a similar IM program>>?

Eldrich [-o<

---

### Post by cacofonix on 2004-11-03
The ubuntu installer does include all the necessary tools to format or resize your hdd and it allows you to specify a swap partition and the file system you want to use. Im not sure about using partition magic to do it but I guess its possible:D, it is a possibility that you could lose your data by resizing your disc partitions as well.


I dont think there is anything other than wine that will run windows programs. You can use all of the instant messaging services in ubuntu with the included Gaim program

---

### Post by Bob D. on 2004-11-03
> does the ubuntu installer provide for creating a swap partition?

Yes.

> can i do the same from partition magic?

Yes. Depending on version you may not get options on different filesystems (ext2, ext3, reiserfs, etc.)

> if i resize my windows partition will i loase my data?

No. But always make a backup before undertaking an action like this, just in case.

> will my windows programs run on ubuntu or suse?

Not directly. Some may run under Wine or CrossoverOffice (non-free version of Wine). If you have some Windows programs you can't find subsitutes for you're going to want to dual boot.

> please tell me if i MSN messenger works in linux

No. Gaim is the very functional multi-protocol IM client that comes with Ubuntu.

Bob

---

### Post by Dennis_k on 2004-11-03
your windows programms wil not work on Linux (exept with VMware) But there are a lot of opensource programs that will doe exactly the same.
you can think about Openoffice for MS office (openoffice coms with the installation of Ubuntu)

Yabber or GAIM for MSN / ICQ / AOL
Evolution 2.0 for microsft outlouk / Outlook express

There's a lot of opensource stuuf out there. some aren't as good as there MS counterparts, and some are better. Remember, opensource is free..

---

### Post by eldrich_rebello on 2004-11-03
ok.thanks so installing ubuntu is'nt gonna be as bad as i thought it would.so now i'm gonna do this when the ubuntu cd arrives:
Burn a back up of all my software
Install suse 9.1 pro
install ubuntu
Please tell me if there might be any issues in doing the above.Does ununtu detect the intel extreme graphics card during install?

Anyone want a corel linux cd?i got one i want to give away to someone with an old computer

Eldrich
Your help has been most useful,specially as there are very few people who are good at these things here in Bombay

---

### Post by cacofonix on 2004-11-03
There shouldnt be a problem with that at all Eldrich :D if one does arise the people on these forums are a bunch of helpful people and will help you sort it out :D

Welcome to Ubuntu by the way :cool:

cacofonix

---

