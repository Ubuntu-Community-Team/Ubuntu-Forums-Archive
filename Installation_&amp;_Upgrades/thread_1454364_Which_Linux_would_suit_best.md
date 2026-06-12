---
title: "Which Linux would suit best?"
date: 2010-04-14
forum: Installation &amp; Upgrades
---

### Post by The Thunder Chimp on 2010-04-14
Hello,
 
I have a friend who wishes to try Linux in Dual-Boot (he wants to keep Windows XP), but unfortunately, his computer is a Super-Lower End computer. I don't think he could install Ubuntu (the original desktop version at least, because of a lack of Random Access Memory. I'd like you to help me choose the best Linux Distribution for this particular computer. I'd also like to say that the computer has two (small) hard drives, C and D.The information I have regarding the computer is the following:
 
Microsoft Windows XP Professional installed on Local Disk C (No Service3 packs), 2002 Version
Intel Celeron Processor
567 MHz
128 MB of RAM
 
Local Disk C: 2,92 GB
Local Disk D: 1,94 GB (free)
 
Thanks.
 
(will it slow down the computer to take the free space on D?)
 
Thanks again!

---

### Post by lvleph on 2010-04-14
Maybe Xubuntu, Arch, or Crunchbang. Windows doesn't like drives that are over 95% full, so keep that in mind.

---

### Post by Romanovzky on 2010-04-14
puppy linux
damn small linux

xubuntu is way to heavy for those specs, I guess even the new unofficial lubuntu is...

you need something really light, I think you won't get any amazing distro since the small linuxes lacks many of those nice features (nice internet repositories, complete working suits, solid media players, etc), but they shall run on those specs :P

---

### Post by cascade9 on 2010-04-14
Dont even try Xubuntu on that system. 

I'd give Puppy a try, though there are others that would work.

---

### Post by Romanovzky on 2010-04-14
And I guess that using drive D won't affect Window$, as it by default puts the spawn dynamic in the drive where the system is installed.

---

### Post by howefield on 2010-04-14
> **Romanovzky said:**
> puppy linux
damn small linux

Is DSL still under development ?

Puppy would likely be a good choice.

---

### Post by Romanovzky on 2010-04-14
actually I don't know, I would go for puppy too.

---

### Post by Anxious Nut on 2010-04-14
I have an IBM computer with the same specs running crunch bang 9.04, and i like it! I had on it ArchLinux first, and it was MUCH FASTER, but it requires a person who's ready to waste his time on it, for the installation(if you have a slow internet connection), configuring, and maintaining. I didn't like puppyLinux and didn't try DSL!

Good Luck

---

### Post by The Thunder Chimp on 2010-04-14
> **Romanovzky said:**
> And I guess that using drive D won't affect Window$, as it by default puts the spawn dynamic in the drive where the system is installed.

Well one of my biggest worries was that maybe Drive D is used as RAM on the computer (by Windows). If I install Linux on Drive D, then that space may (or may not) be inaccessible to use as RAM by Windows.

What about Slitaz? Would that be a good option? Is Lubuntu out of question?

I'd like it to be Debian based (if possible) too, so I can better help him. Is that possible?

Thanks Guys!

---

### Post by Romanovzky on 2010-04-14
Well, you most know where the winxp is allocating the swap (and not spawn as I've previously mentioned), try this link for more info

[http://www.aumha.org/win5/a/xpvm.php](http://www.aumha.org/win5/a/xpvm.php)

As far as I know, you can see the configuration in winxp and change it.

But don't worry too much, the swap is only use when RAM is full, and as long as you don't use winxp to run high-end software it may never be actually used.

For the linux distro, search the web, I did and found out

[http://lightlinux.blogspot.com/2008/06/top-10-of-lightweight-linux_24.html](http://lightlinux.blogspot.com/2008/06/top-10-of-lightweight-linux_24.html)

And I again recommend Puppy.

Slitaz is a USB/LiveCD-only runnig, i.e., it is not meant to be installed on hard drives. Hence the name: SliTaz - Simple Light Incredible **Temporary Autonomous Zone**.

---

### Post by Romanovzky on 2010-04-14
I amend my previous comment, Slitaz may be installed (overloked the web :P).

Don't know how it works, give it a try and then tell us :P

[http://en.wikipedia.org/wiki/SliTaz_GNU/Linux](http://en.wikipedia.org/wiki/SliTaz_GNU/Linux)

---

### Post by The Thunder Chimp on 2010-04-14
Okay, I'll try to look into that. You could check this out though, it's a page on Lubuntu. It says that it might be good on Celeron with 128 MB of RAM.

"A Pentium II or Celeron system with 128 Mb RAM is probably a bottom-line configuration that may yield slow yet usable system with Lubuntu."

-Source: [https://wiki.ubuntu.com/Lubuntu](https://wiki.ubuntu.com/Lubuntu)

What do you guys think?

---

### Post by The Thunder Chimp on 2010-04-14
> **Romanovzky said:**
> I amend my previous comment, Slitaz may be installed (overloked the web :P).

Don't know how it works, give it a try and then tell us :P

[http://en.wikipedia.org/wiki/SliTaz_GNU/Linux](http://en.wikipedia.org/wiki/SliTaz_GNU/Linux)

Yeah, I tried it on my USB stick a while ago and there was this Desktop Icon that said "Install Slitaz".

---

### Post by gunnarlinux on 2010-04-14
> **The Thunder Chimp said:**
> Hello,
 
I have a friend who wishes to try Linux in Dual-Boot (he wants to keep Windows XP), but unfortunately, his computer is a Super-Lower End computer. I don't think he could install Ubuntu (the original desktop version at least, because of a lack of Random Access Memory. I'd like you to help me choose the best Linux Distribution for this particular computer. I'd also like to say that the computer has two (small) hard drives, C and D.The information I have regarding the computer is the following:
 
Microsoft Windows XP Professional installed on Local Disk C (No Service3 packs), 2002 Version
Intel Celeron Processor
567 MHz
128 MB of RAM
 
Local Disk C: 2,92 GB
Local Disk D: 1,94 GB (free)
 
Thanks.
 
(will it slow down the computer to take the free space on D?)
 
Thanks again!

Try Puppy Linux or DSL. Probably the best suit. Or just tell him to spend a little money and upgrade that RAM and hard drive :lolflag:

---

### Post by cascade9 on 2010-04-15
> **The Thunder Chimp said:**
> Well one of my biggest worries was that maybe Drive D is used as RAM on the computer (by Windows). If I install Linux on Drive D, then that space may (or may not) be inaccessible to use as RAM by Windows.

What about Slitaz? Would that be a good option? Is Lubuntu out of question?

I'd like it to be Debian based (if possible) too, so I can better help him. Is that possible?

Thanks Guys!

Unless you change the page-file location, its always on C:. 

Lubuntu might work (as would debian lxde). I'm not sure about how much junk they left in lubuntu though. 

If you really want a debian-based distro, try crunchbang.  

You could always just find another 128/256MB RAM and then you've got a lot more choices. ;)

---

### Post by The Thunder Chimp on 2010-04-15
> **cascade9 said:**
> You could always just find another 128/256MB RAM and then you've got a lot more choices. ;)

Yeah, I've thought of that myself, but you see, the thing is, everything is working fine on his Windows XP (slow but fine), so it would be kind of awkward to tell him:

"Hey, Linux is the best thing that could ever happen to your computer. It only requires you to double the RAM you currently have."

He might do it later, but first, he'd like to try it out.

Debian LXDE might not be to harsh for a beginner?
Do you think Lubuntu will become official anytime soon?
I'll look into Crunchbag and come back to you!

Thanks again.

---

### Post by cascade9 on 2010-04-16
> **The Thunder Chimp said:**
> Yeah, I've thought of that myself, but you see, the thing is, everything is working fine on his Windows XP (slow but fine), so it would be kind of awkward to tell him:

"Hey, Linux is the best thing that could ever happen to your computer. It only requires you to double the RAM you currently have."

He might do it later, but first, he'd like to try it out.

I see your point, but from what I remember when I tried a P3 system (866, so a bit faster CPU than your friend has) it seemed faster with Debian Xfce than it did with XP. 

XP, Xfce, or LXCE will all run a lot better, and faster, with 256MB/384MB than with 128MB. 

> **The Thunder Chimp said:**
> 
Debian LXDE might not be to harsh for a beginner?
Do you think Lubuntu will become official anytime soon?
I'll look into Crunchbag and come back to you!

Thanks again.

Well...Debain testing/unstable migth be a bit harder than a 'stable' debain release. I dont think I would try that for a beginner (but I'm sure people have done it and got away with it fine). A stable debian version (currently 'lenny') would be not that much harder than ubuntu (if any harder at all)- the only difficult bit would be 'remember to get your updates'. I'm pretty sure that the update-notifier from ubuntu can be installed on debian, and then it would be pretty much the same. 

Once you've got the system setup there isnt much to do other than use the system. 

As for lubuntu becoming 'offical', no idea. 

Good luck with crunchbang ;)

---

