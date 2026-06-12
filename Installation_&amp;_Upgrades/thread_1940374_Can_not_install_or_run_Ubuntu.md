---
title: "Can not install or run Ubuntu"
date: 2012-03-13
forum: Installation &amp; Upgrades
---

### Post by Vynesh on 2012-03-13
Hi! I'm a first time linux user and not an AMAZINGLY tech savvy person, so please be patient with me :(
 
I have tried installing with Wubi, booting from a LiveCD, and turns out I don't have the bios for booting from a pendrive either. Wubi says it's installed, but I have no idea how to run Ubuntu. I've restarted possibly hundreds of times over the last two days trying to figure out why it won't give me the option to boot from either windows or Ubuntu. It just loads windows automatically. I've tried using some 3rd party boot manager, but it turns out I don't have Ubuntu on a partition? No idea how to set that up either. 
 
I tried the LiveCD, but after changing my bios to boot from the cd rather than the hdd I get a short boot message about loading linux, shortly after that two little icons appear on the bottom of my screen then after a few seconds the screen goes black and blue squares start flickering all over the screen. No sounds. No messages. Just flashing random blue squares all over my screen. I've made 7 LiveCDs/DVDs, but to no avail I can not get this OS to run alongside windows, or to replace windows. I'm beginning to think it's a hardware problem but I'm not sure. :confused:
 
Please help! I've been trying to figure this out for awhile now and unfortunately I lack the experience and knowledge to even install it apparently! /repetativefacetodesk

---

### Post by Rex Bouwense on 2012-03-13
Interesting.  First, what are the specifications of your computer and what version of Microsoft Windows are you running?
Do you have any problems booting and/or running Windows?
By the way welcome to the forums.:popcorn:

---

### Post by Vynesh on 2012-03-13
I'm at work at the moment, so I'm sorry if this isn't enough info!
 
I on a Compaq (not sure of the model as it was a freebie) But I've got a 2.9 GHz Celeron D, 1.5 gig RAM, and 180gb hdd. Running on Windows XP Home, sp3 32 bit.
 
Not at all! I can get Windows to boot and run without any problems.
 
And Thank you! I look forward to learning, and teaching others here when I am worthy! haha.

---

### Post by Vynesh on 2012-03-13
> **Vynesh said:**
> I'm at work at the moment, so I'm sorry if this isn't enough info!
 
I on a Compaq (not sure of the model as it was a freebie) But I've got a 2.9 GHz Celeron D, 1.5 gig RAM, and 180gb hdd. Running on Windows XP Home, sp3 32 bit.
 
Not at all! I can get Windows to boot and run without any problems.
 
And Thank you! I look forward to learning, and teaching others here when I am worthy! haha.
 
 
There's a setting in System Properties/Advanced/Startup and Recovery to display other OS's and display timers. I over looked this, and I will report back when I am able to give it a try!

---

### Post by Mark Phelps on 2012-03-13
> **Vynesh said:**
> I have tried installing with Wubi, booting from a LiveCD, and turns out I don't have the bios for booting from a pendrive either. 
You don't install using Wubi from the CD; instead, you boot into Windows, insert the CD, and install it from there.  It uses Windows to do the install.

> Wubi says it's installed, but I have no idea how to run Ubuntu. 
How does it "say" this, meaning, how do you know that it actually installed.  You should see an entry under Program and Features (in Win9) listing Ubuntu as an application.

> I've tried using some 3rd party boot manager, but it turns out I don't have Ubuntu on a partition? No idea how to set that up either.  Wubi doesn't install to its own partition; instead, it installs inside an existing NTFS partition.
 
> ... blue squares start flickering all over the screen. No sounds. No messages. Just flashing random blue squares all over my screen.  Possibly an incompatible video card/chipset.

> I can not get this OS to run alongside windows, or to replace windows.  If your PC came preinstalled with Win7, then it likely already HAS the maximum of four primary partitions configured on the drive.  If that's the case, the installer can't create any more and won't offer you the side-by-side option.

---

### Post by Vynesh on 2012-03-13
> **Mark Phelps said:**
> How does it "say" this, meaning, how do you know that it actually installed. You should see an entry under Program and Features (in Win9) listing Ubuntu as an application.
 
I searched windows for Ubuntu with hopes of finding some kind of launcher, showing hunreds of files of course. Then I attempted to reinstall it via Wubi, and it asked if I wanted to replace my current version. Sorry about not being descpitive on my first post! I didn't want it to be a novel lol.
 
> Wubi doesn't install to its own partition; instead, it installs inside an existing NTFS partition.
 
I still have much to learn about partitions, and thank you for telling me! Would it be ideal to create a partition solely for Ubuntu? or to keep it on the same partition with Windows?
 
> Possibly an incompatible video card/chipset.
 
Crap. I'm pretty positive it's running on the chipset. I have a spare video card laying around, I'll slap that in there asap!
 
> If your PC came preinstalled with Win7, then it likely already HAS the maximum of four primary partitions configured on the drive. If that's the case, the installer can't create any more and won't offer you the side-by-side option.
 
I'm on Windows XP Home for the time being. I don't think I've ever had this much trouble with software haha. 
Unfortunately I am at work or I'd be trying all of these suggestions! In a few hours I will be able to have it in front of me. I apologize for posting my issue before having it on hand! You guys respond to issues incredibly fast haha. I can not convey the thanks I have for everyones help!

---

### Post by Vynesh on 2012-03-13
Ok, I'm at my home station now. Turns out the check box in System Properties fixed my booting problem, but I'm still getting those blue squares after I choose Ubuntu. Any tips on solving this? I'm not sure if there's a way to MAKE it compatible with drivers or settings, but I'll see what I can do.

---

### Post by Vynesh on 2012-03-13
Since this has become a hardware issue, and the booting/installing seems to have been figured out; I'm going to mark this thread as solved and recreate a thread in Hardware for the display issues. Thank you guys for all the help and information! :)

---

