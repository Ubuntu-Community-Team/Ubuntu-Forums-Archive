---
title: "Instalation FAILED (Partitions!)"
date: 2006-06-01
forum: Installation &amp; Upgrades
---

### Post by chris062689 on 2006-06-01
Ok, I've been using Ubuntu for quite a while, and love it.
I recently had switched back to windows, for application reasons, but then decided to duel boot once this new version came out.

I partition all of my computer all nice and neat with QParted, then the QParted messed up, lost Windows XP.  ](*,) 

So then, I was like, What the Heck, why not install Ubuntu and run Windows 98 inside of Ubuntu with a emulator.  Sounds good, right?

Well, I ran through the new (shiny) setup, and when I went to partition it, (I choose the "take over my hard-drive totally" function) it came back with an error (about 15% of the way) saying that it failed to create a partition.

I'm thinking I should run fdisk, to fix this, would it help? (if so; how would I corretly run it)

It's always worked in the old style installer, is there anyway I could try that?
I'm downloading kubuntu right now, if that installer fails, then I will try suggestions posted here.

---

### Post by supirman on 2006-06-01
I got anerror at 15% too, but mine said "can't create filesystem".   It seems like there is certainly a nasty bug in there somewhere........

---

### Post by chris062689 on 2006-06-01
[QUOTE=supirman]I got anerror at 15% too, but mine said "can't create filesystem".   It seems like there is certainly a nasty bug in there somewhere........[/QUOTE]

What type of computer do you have?
I have a HP Pavilion a305w.
Running on a 180GB hard-drive (posiblly corrupted?)

It installed fine in the other linux distro I used (Puppy Linux) so I doubt it's corrupted, but it could have some kind of error.
That's why I want to run fdisk.

Just don't know HOW. ](*,)

---

### Post by supirman on 2006-06-01
I tried installing it on my old toshiba laptop.  It's currently running Fedora Core 5, but Dapper won't install.

---

### Post by chris062689 on 2006-06-01
Have you tried Kubuntu?
I find it weird that it stoped working when the new installer was put in.
Is there anyway to revert to the old installer?

---

### Post by supirman on 2006-06-01
I've not tried downloading kubuntu.  I'm running kubuntu on my desktop, but that was upgraded from 5.10, not a fresh install.  It fails on creating the filesystem, which is odd.  I went to System->administration->disks and it detected my hard drive fine, showed it's size fine, etc.  But when I try to install, it pukes out.  Wow, this is annoying.

---

### Post by chris062689 on 2006-06-01
Hmm...
Well I'm downloading Kubuntu now, I will tell you how it goes if it's sucessful.

---

### Post by supirman on 2006-06-01
Well, mine just got passed the previous point.  The problem was apparently that Fedora 5 set up LVM on my disc, and the "desktop" installer seemingly can't handle that. I used fdisk to erase my whole hard drive, then rebooted and tried the installer again.  It's on 28% right now....

to run fdisk, go to applications->accessories->terminal   
then 
fdisk /dev/hda (if hda is your hard disk)

---

### Post by caps on 2006-06-01
all I had to do was restart in safe graphical mode after it said it failed to create filesystem

hope this helps... I know it seems kind of sketchy, but it worked

-James DeLong

---

