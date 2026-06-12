---
title: "I need XP back, Im going crazy!"
date: 2007-09-16
forum: Installation &amp; Upgrades
---

### Post by sam510 on 2007-09-16
Alright well I really liked ubuntu, but It didnt support the games I played. So ive decided to keep ubuntu but go play my games in vista. I tried booting XP from the grub loader and it just hangs at Starting up.. Now i've tried to go repair it the fixmbr command, but It would just give me an error when It tried to load the windows boot loader. It would say Disk read error press ctrl+alt+del to restart. Ive downloaded and burned over 5 CD boot disks, I can succesfully but back into ubuntu but whenever I try to use the same software to boot into the windows partition it still hangs there. I know for a fact which partition XP is in but it just wont boot on any kind of boot loader, I'm very confused and im 100% sure its not a hardware issue. Before I installed ubuntu XP would boot fine.

---

### Post by madhatter64 on 2007-09-17
I am a fellow XP gamer. My advice is to post the problem in a Windows or Microsoft support Newsgroup. I have had issues with Linux/MS conflicts and the MS team is usually very friendly and supportive as well as helpful. 

Post your problem in microsoft.public.windowsxp.help_and_support for starters.

I wish I could tell you how to fix your problem, but I this is my best suggestion. 

Let us know what happens next. 

MH

---

### Post by Lord Landis on 2007-09-17
It sounds like your system is (mostly) borked, so why not nuke & do a clean re-install?

It's been my experience that a dual-boot system is easier to set up if you install Windows to the entire drive first and then install Linux & resize the partition to suit your needs.  YMMV, but I've done three systems like that and never had a problem with any of them.

---

### Post by r76 on 2007-09-17
> **sam510 said:**
> ive decided to keep ubuntu but go play my games in vista
> **sam510 said:**
> I tried booting XP from the grub loader and it just hangs at Starting up.
Are you triple booting Vista, XP and Ubuntu?  Just trying to work out which boot-loader you need working...

---

### Post by Pumalite on 2007-09-17
I agree with Lord Landis.

---

### Post by SteveHillier on 2007-09-17
> **r76 said:**
> Are you triple booting Vista, XP and Ubuntu?  Just trying to work out which boot-loader you need working...
This was not an issue when I did it.  
I had an XP machine.  I loaded Ubuntu.  I then loaded Vista onto a new HDD.  OK is screwed up the GRUB loader but I reinstalled Ubunut and it worked fine.
GRUB said do you want to boot into Linux and at the bottom said 'Other Operating systems' and listed XP.  I selected that and the Windows boot loader said do you want Xp or Vista and got on and did it.
I no longer have Vista on that maching but that is a different story - I took it off for not technical reasons.

---

### Post by Druke on 2007-09-17
when you try to boot xp, does it actually get to the xp loader splash?

---

### Post by inik on 2007-09-17
if you have your systems on separate drives, check boot.ini file on windows partition, maybe you change disk order when installing linux

---

