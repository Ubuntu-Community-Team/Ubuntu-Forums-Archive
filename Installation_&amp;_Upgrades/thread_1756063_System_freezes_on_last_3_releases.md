---
title: "System freezes on last 3 releases"
date: 2011-05-11
forum: Installation &amp; Upgrades
---

### Post by Baasha on 2011-05-11
I have been a happy Ubuntu user for several years.  But I am stuck with version 9.10 because of a persistent problem with random lockups with both mouse and keyboard.  A search on the forums both within and without the Ubuntu community shows that a lot of other people have this same problem.  There have been a lot of suggestions given and I have tried everything I could find, but without success.  I have tried clean installs of vs. 10.04, 10.10, and 11.04 but all have the same problem.

The computer will work fine for a few minutes to a few hours and then just lock up.  The only way out is a hard reset.  Someone suggested that the latest versions of Ubuntu have a problem with some of the newer Intel chipsets, but I don't know enough to be able to say one way or the other.

I am running an ASUS P7P55D motherboard with a 4 core Intel i5 processor and an Nvidia graphics card. I have tried the latest version of the bios for the P7P55D but that hasn't helped either.  Vs 9.10 is no longer supported and I am being left behind.  Can anyone point me in the right direction to overcoming this problem?

---

### Post by silbar on 2011-05-11
I am using 10.04 and am having the same random freeze-ups, mopuse-click and keyboard, requiring a hard power-down/up to restart.  (Bad, I understand, but nothing else seems to work.).  Looking at the logs at the time of the freeze does not provide any clues as to what goes wrong. 

Any solution to this problem (which, as Baasha and others say, also occurs in 10.10 and later)?

I am using an HP Pavilion with nothing special other than what the computer came with.  It seems to be happening most often when I am wating time with KPatience solitaires.

   Rico Silbar

---

### Post by norm.h on 2011-05-13
I'm having similar problems, my screen will freeze at random, regardless of what I'm doing, or it might freeze during the boot process. 
Like others, a hard reset cures the problem.
I'm running 10.10, but never had the problem with 10.04, 9.10, or 9.04.
Strangely enough, my wife runs 10.10 on her lappie, and daughter runs 10.04 on hers, but neither are experiencing this problem.

---

### Post by Baasha on 2011-05-17
Is there anyone out there who is knowledgeable enough to at least tell me where to start with this problem?  A search of Launchpad turns up no definitive fix.  Many people seem to be having the same problem but the developers haven't seen fit to up the priority of this bug even though it has spanned 3 (or maybe 4 releases; haven't tried 11.10 yet).

As reported many times, those that have the problem don't have much to report in the way of log entries because no obvious errors are recorded in the logs.

---

### Post by NormanFLinux on 2011-05-17
Try a kernel upgrade... most often the current kernel is interfacing badly with installed hardware and a new kernel will run better with it.

2.6.39.0 is the one to go with Natty Narwhal.

---

### Post by Dutch70 on 2011-05-17
You can try post#22 of the link in my sig. Even though the thread is titled with a different graphics card, it works for some others as well. Even though it may sound a little silly,(as in removing compiz then adding it back) it works perfect on my pc with several different Linux OS's. Without it, I wouldn't even be able to use Ubuntu, Kubuntu, Linux Mint or some others that I've tried.

---

