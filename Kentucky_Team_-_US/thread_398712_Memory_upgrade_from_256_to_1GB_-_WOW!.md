---
title: "Memory upgrade from 256 to 1GB - WOW!"
date: 2007-04-01
forum: Kentucky Team - US
---

### Post by JarG0n on 2007-04-01
I just upgraded my system from 256 to 1GB, and the performance difference is nothing short of phenomenal !  I noticed paging in System Monitor, but now I have 0 paging with 1GB + 256MB.  

Edgy really doesn't run all that well with just 256.  I don't understand it either.  I never see it fully utilize 256MB at any point.  Why not?

---

### Post by zenwhen on 2007-04-10
More ram = less paging. Less paging = less system chug.

Nice upgrade.

---

### Post by etank on 2007-04-11
I wish I could afford a memory upgrade. My system seems to run OK with 512MB though. 2Gig would be better though :wink:

---

### Post by az on 2007-04-11
> **JarG0n said:**
> 
Edgy really doesn't run all that well with just 256.  I don't understand it either.  I never see it fully utilize 256MB at any point.  Why not?

Even if you only have the very minimum amount of ram, it would never use 100 percent of it.  It would always dump whatever it can out of what it has cached when it would need more ram to start a new process.  Your computer would not be able to work otherwise.

The linux kernel will always try to cache as much as it can into ram so that the system runs faster.  On the other hand, if you are short on ram, it will not be able to cache that much and your performance will suck since it will have to load the same libraries over and over as it tries to get stuff done.

---

### Post by Koji-Murasame on 2007-04-11
My main desktop has 1.5 GB (really comes in handy when running lots of stuff at once) and I just upgraded my HP Pavilion 4430 form 96 MB to 256 MB.

---

### Post by JarG0n on 2007-04-11
> **zenwhen said:**
> More ram = less paging. Less paging = less system chug.

Nice upgrade.

Right!  But, why decide to page when all available RAM hasn't come close to being consumed?  This is what's confusing me.

---

### Post by dasunst3r on 2007-04-11
I went from 512 MB on my previous computer to 2 GB on my new one.  Indeed, my swap has never been used before and I now use the preload application to make my computer pretty snappy. :)

---

### Post by JarG0n on 2007-04-11
> **az said:**
> Even if you only have the very minimum amount of ram, it would never use 100 percent of it.  It would always dump whatever it can out of what it has cached when it would need more ram to start a new process.  Your computer would not be able to work otherwise.

The linux kernel will always try to cache as much as it can into ram so that the system runs faster.  On the other hand, if you are short on ram, it will not be able to cache that much and your performance will suck since it will have to load the same libraries over and over as it tries to get stuff done.

I still don't understand why it never attempts to use 100% though.  It's kindof disappointing really.  I thought linux was supposed to be less resource intensive.  I suppose it depends on what you have loaded, of course.  I doubt it will ever consume as much RAM as Vista needs for all the spyware and bloatware :D

---

### Post by voided3 on 2007-04-11
I ran Xubuntu on a 450mhz AMD K6-III system with 192mb of ram and it never had any problems, even when running Quake III Arena! It used only 60mb at boot w/ 0 swapping and i'd only really use firefox, gaim, and beep media player with it. The only time I ever really saw it cache up a lot was when playing quake, but even then it was only about 50mb. If I had used it for multitasking, I know I would have ran into some slow downs though. I also currently run Xubuntu on a 700mhz Intel Celeron Coppermine system w/ 384mb and a nvidia mx440 and that is more than plently; I get an average of about 80 fps in Planet Penguin Racer! My main desktops have 832 and a gig of memory though and run regular Ubuntu... lets just say i was considering deleting my swap partition since it never gets used haha (though I know that's a bad idea). I also run Ubuntu on my Macbook Pro in VMware Fusion and even though it has 2gig, I only allotted the VM 640mb since, once again, that swap partition just doesn't get used. Typically on Ubuntu there only is about 110mb used at boot so 512mb would be more than sufficient for the average user IMHO. Moral of the story though, if you can afford it and plan on actually using the system, get as much RAM as possible!

---

### Post by RJARRRPCGP on 2007-04-11
> **JarG0n said:**
> I just upgraded my system from 256 to 1GB, and the performance difference is nothing short of phenomenal !  I noticed paging in System Monitor, but now I have 0 paging with 1GB + 256MB.  

Edgy really doesn't run all that well with just 256.  I don't understand it either.  I never see it fully utilize 256MB at any point.  Why not?


But, be careful. You may be required to take the 256 MB RAM module out for the OS to not get corrupted. 

I was working on a PC and added 2 256MB RAM modules and then after I was done working on it, the owner complained about it rebooting over and over again. 

Also, another PC, which I still own, after I added another 128 MB PC133 SDRAM module, after I turned it on one day, which had Windows XP or Windows 2000 on it, got the dreaded STOP: INACCESSIBLE_BOOT_DEVICE BSOD. Both of the PCs that crashed recently had a RAM module added. 

It seems that even when Memtest86 passes, the OS can silently get corrupted.

---

### Post by montgoej on 2007-04-11
Lucky...I wish I had the money to upgrade from 512 to 1g on my main machine. The computer I'm writing this from right now is running the dreaded *WINBLOWS XP* on 256megs and I can't run more than 3 or 4 programs or BSOD...
~Jordan Montgomery

---

### Post by Koji-Murasame on 2007-04-12
> **montgoej said:**
> Lucky...I wish I had the money to upgrade from 512 to 1g on my main machine. The computer I'm writing this from right now is running the dreaded *WINBLOWS XP* on 256megs and I can't run more than 3 or 4 programs or BSOD...
~Jordan Montgomery

There are lots of small linux distros that will run on that no problem.

---

### Post by az on 2007-04-12
> **JarG0n said:**
> I still don't understand why it never attempts to use 100% though.  It's kindof disappointing really.  I thought linux was supposed to be less resource intensive. 

Well, linux uses more ram than windows does because there is no point in leaving ram free for the sake of leaving ram free (like windows seems to do).

It's just a fact of life that you will always have to keep a small amount free so that you can actually do new stuff at any time.  It's not always feasable to fit the chunks of ram you need to fill 100 percent.


> **RJARRRPCGP said:**
> But, be careful. You may be required to take the 256 MB RAM module out for the OS to not get corrupted. 

I was working on a PC and added 2 256MB RAM modules and then after I was done working on it, the owner complained about it rebooting over and over again. 

Also, another PC, which I still own, after I added another 128 MB PC133 SDRAM module, after I turned it on one day, which had Windows XP or Windows 2000 on it, got the dreaded STOP: INACCESSIBLE_BOOT_DEVICE BSOD. Both of the PCs that crashed recently had a RAM module added. 

It seems that even when Memtest86 passes, the OS can silently get corrupted.


I don't know what you mean by "OS gets corrupted".  If you put in faulty ram, your computer won't boot regardless of the OS.  

And memtest will properly assess your ram.  It is the most reliable and sensitive way to check ram.  I suggest you had hardware problems after you checked the ram.

You won't convince me that you have faulty ram that will pass memtest86.  That can't be.

---

### Post by montgoej on 2007-04-13
> **Koji-Murasame said:**
> There are lots of small linux distros that will run on that no problem.

Yeah, I'd actually like to put Linux on that computer, but it's my parents' computer and they won't even try Linux.
~Jordan Montgomery

---

### Post by Landshark on 2007-04-15
Why is one of Bunny's eyes bigger than the other?  Is this a birth defect..?

Poor Bunny.

---

### Post by JarG0n on 2007-04-17
> **Landshark said:**
> Why is one of Bunny's eyes bigger than the other?  Is this a birth defect..?

Poor Bunny.

It's from TMS syndrome (Tyrant Madness Syndrome)

---

### Post by old_geekster on 2007-04-17
Memory has always been the best bang for the buck, when it comes to performance enhancement.  You will definitely enjoy computing much more.

---

### Post by annihilus06 on 2007-04-18
Went from 512 to 2GB at work the other day after explaining to them that my time was their money.  I got the upgrade and am loving every minute of it.  Definitely notice the difference.  I had previously upgraded my laptop from 512 to 1GB but the jump from 512 to 2GB was like i was on a whole new computer at work.

---

### Post by annihilus06 on 2007-04-18
Oops double post,  apologies

---

### Post by JarG0n on 2007-04-19
> **JarG0n said:**
> It's from TMS syndrome (Tyrant Madness Syndrome)

Correction.  That's TNS (Tyrant Narcissist Syndrome).  :)

---

