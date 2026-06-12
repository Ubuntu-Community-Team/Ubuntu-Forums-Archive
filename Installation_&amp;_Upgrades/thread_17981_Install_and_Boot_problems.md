---
title: "Install and Boot problems"
date: 2005-03-03
forum: Installation &amp; Upgrades
---

### Post by Bruce Peterson on 2005-03-03
I have been playing around with Knoppix and Gnoppix and finally decided to go ahead and do a Ubuntu install on an older Gateway machine.  I burned the 386 ISO and proceeded to install it.  When asked about the partition I opted to do the complete repartition with a clean install.  I finished up the install and it told me to remove the cd from the drive and it would re-boot into my new ubantu installation.  When it got half way through the Gateway load splash screen it locked up and that it is where I am stuck.  It will not boot to any of the live cd distros or to the Ubantu install disk.  What do I do?

---

### Post by bored2k on 2005-03-03
Your "machina" not booting any CD i wouldnt think its a problem with Ubuntu , mainly bcuz that happens right before the HDD's OS b0_ot takes place, i were id look up in the bios setup, or maybe juggle with a recovery disc like Hiren's .

---

### Post by Bruce Peterson on 2005-03-03
I am not able to get to the BIOS settings.  ](*,)

---

### Post by bored2k on 2005-03-03
[QUOTE=Bruce Peterson]I am not able to get to the BIOS settings.  ](*,)[/QUOTE]


 :-o 

Hitting DEL key "like ur gonna get 100dollars everytime u press it like crazy"just as the box is starting doesnt work? or F8 or F12 or whatever ur box uses?

"mos deF" thats not a distro problem ___

or maybe its passwd protected and u dont hav access to it  8-)  [-(

---

### Post by Bruce Peterson on 2005-03-03
Nope, none of them work.  When I tap Tab I get a message screen which shows all the detected drives and the USB mouse and keyboard.  Thats all I can get to.

---

### Post by Gary Powers on 2005-03-03
Bruce, I had a similar problem with an eMachine, which coincidentally is made by Gateway (I think).  In order to get to the BIOS, disconnect the drive and boot it.  Not sure what you will find under hard drives, but if you can switch the HD from AUTO to LBA it might work.

After losing three drives (they do work in other boxes), I replaced the motherboard in the eMachine and all is well.

I started messing with Linux in early December and have bought/built four computers since then.  So it may be free, but it aint cheap! ;) 

Have fun and keep us posted on your progress.

Gary

---

### Post by Bruce Peterson on 2005-03-03
Well I pulled the drive out of the machine and it would then boot to Knoppix.  So I think I am going to try to find a cheap 20 gig drive and start all over.  Thanks for all the help guys.

---

### Post by bored2k on 2005-03-03
[QUOTE=Gary Powers]Bruce, I had a similar problem with an eMachine, which coincidentally is made by Gateway (I think).  In order to get to the BIOS, disconnect the drive and boot it.  Not sure what you will find under hard drives, but if you can switch the HD from AUTO to LBA it might work.

After losing three drives (they do work in other boxes), I replaced the motherboard in the eMachine and all is well.

I started messing with Linux in early December and have bought/built four computers since then.  So it may be free, but it aint cheap! ;) 

Have fun and keep us posted on your progress.

Gary[/QUOTE]


what ?! are eMachines that crappy ?!?

i thought i had read on PC-Mag they were xtremely realiable for their cost !!!

---

### Post by pigpen on 2005-03-04
Is the eMachines the company that puts in refurbished parts in the computer, so they can offer it cheap?

I knew a guy who worked at one of those companies and it told some funny (and scary) stories about the kind of (old) parts they put in. And I think it was eMachines he worked at.

---

### Post by Gary Powers on 2005-03-04
Bruce, make sure to set your HD to LBA before you reinstall Ubuntu.

Bored, I actually like the little eMachine and it worked fine under XP or when I was dual-booting using the LILO boot loader (Mandrake and Slackware), but it sure did not like GRUB!

Gary

---

### Post by Bruce Peterson on 2005-03-04
Will do.  Thanks again.

---

### Post by New10 on 2005-04-21
Towards the end, this thread turned into a discussion on the merits of eMachines.

I bought  2 eMachines. 
1st eMachine: Pentium 4, 512 MB, 160 GB, running windows XP home edition. Except for the Microsoft cripple Windows XP Home Edition, I have been extremely pleased with the eMachine. I liked it so much that I bought a second one.

2nd eMachine: AMD Athlon 64, 512 MB, 160 GB.  I decided to run an all Linux PC. I removed all the Windows partitions and installed Linux.  First I installed Mepis on automatic install. Mepis installed fine, but it would not recognize the eMachine audio or ethernet hardward.  After a ton of Mepis posts and sweat and frustration, I did a complete reinstall with Ubuntu 64.  On the first boot, the sound came on (a very good sign that Ubuntu might be recognizing more of the eMachine hardware).  But, very shortly after login, the PC froze on the brown screen.  Hmm... other people post about freezing on the brown screen.  I'll try installing Ubuntu 32 next.  If the problem persists, I may be moving on to anther distro.

---

