---
title: "Alternate cd and live cd can't boot after install"
date: 2006-08-07
forum: Installation &amp; Upgrades
---

### Post by joople on 2006-08-07
Hi all.  
Here's my stuation that I've been trying to figure out all weekend. 

I only have one hard drive that I want to install Ubuntu on. Everything installs perfectly. on both install cd's, but when I reboot after install.  I get "DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER." Keep in mind I can install windows xp on this hard drive with no problem I just did it this morning and yesterday. So the hard drive is fine. It has 20gigs. 

What do I do?  I have tried everything.

Previously I had another hard drive that has windows xp on it and I tried to creat a dual boot setup, but nothing was working; getting the exact same error message.  So at the momment I am only using one hard drive the other hard drive is disconnected completely.  I only care about now is to get Ubuntu installed on this stinkin' hard drive.  If I can do that then I can figure out the the whole dual boot thing later. 

Oh by the way when I had Windows XP on this harddrive yesterday I also setup a dual boot on this hard drive. So making for windows on half the disk and Ubuntu on the other half. and still no go. GRUB just stalls and gives an error 25 message; meaning "Disk Boot Failure" So this tells me where ever Ubuntu installs it's acting like it created a bad sector somehow and/or whatever that means.

Sorry for the long response. I just wanted anyone who can help to have all the facts. This is driving me NUTS! ](*,)

---

### Post by joople on 2006-08-07
Oh I also forgot to mention That yes I checked the ISO; md5summer. and I burned both cd's at 4x and 10x just to make sure.

---

### Post by kannasama on 2006-08-07
Did you make sure to install GRUB or LILO to the Master Boot Record, of /dev/hda (or hd0)

---

### Post by joople on 2006-08-07
Yes I installed and re-installed many many times to MBR. I re-installed on both ALternate CD and Live CD.  I don't think that Grub is the problem.  Thanks for the reply.  I followed so many different install instructions it's ridiculus.  Somehow I need to think outside the box here. Please someone figure this out.  there are other websites and forums with this proplem and none of them can figure it out.  Everyone just gives up.  I will never give this up. Please help.  

Maybe for some reason the hard disk isn't being activated who knows.   I know that Ubuntu got installed because I can see it when I sudo it in the terminal on the live CD. everything looks correct.

---

### Post by joople on 2006-08-08
Someone has to have an answer for this? No one?

---

### Post by joople on 2006-08-09
Bump.............??????

---

### Post by randell6564 on 2006-08-09
I'll try and work with you as much as I can, my Friend.  I have dual-booted in the past with no problems from iso's and cd's from ubuntu.

If you are not concerned with XP, I would completely Wipe the drive (just because I want to eliminate any possible reasons!)

Then, I would get a dos boot disk (you can get one online) and do a fdisk MBR
This will rewrite the MBR. I know, you already said that you are not having any problems booting into Windows, but just entertain me!

This way you are starting with a clean HD.  Now Reinstall ubuntu and towards the end of the install, you should get an option to install Grub to the MBR. say Yes.  (although, depending on what installation disk you are using, you might not get the option)  I'm pretty sure that if you are using an iso that you downloaded from, say [www.distrowatch.com](www.distrowatch.com) you will get the grub option.

Try it!

---

