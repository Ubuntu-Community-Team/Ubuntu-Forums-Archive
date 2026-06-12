---
title: "Newbie having install problems"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by ChiefOfSages on 2006-10-27
Hello.  I'm a Linux/Ubuntu newbie trying to do a clean install of 6.10 on an Inspiron 6000 (Pentium M Dothan).  My problem is when I try to boot off the Live CD.  My CD drive spins up, then spins down, then up again, and so on, for about 5 minutes.  I get a few errors here and there saying "Buffer I/O error on device sr0."  Then eventually I get an "hw_random: cannot enable RNG, aborting" before the Live CD finishes booting.  Takes about 10 minutes, I think.

After a bit of Googling, I got the impression that the sr0 referred to my CD drive (Sony CDRW/DVD CRX835E).  I'm not 100% sure though.  After those errors, I wasn't so sure about installing.  And what's up with the RNG error?  What hardware issue would cause that?  Lol.

Anyway, I'd appreciate any help I could get on this issue.  Thanks! :)

---

### Post by vibestriton on 2006-10-27
Sounds like a corrupted disk or .iso (if downloaded) to me.  

If you still have the iso try checking it with md5sum.  Make sure the result [matches]("http://releases.ubuntu.com/6.10/MD5SUMS").

---

### Post by ChiefOfSages on 2006-10-27
Thanks for the response.  I did the following:

1. MD5 checked the .iso;
2. verified the disc after burning; and
3. verified the disc from within the Ubuntu bootup screen.

I should also add that I am not trying to boot this Live CD off of a freshly reformatted computer.  I'm just trying to get the Live CD to work.  THEN I'll reformat.

---

### Post by paul85 on 2006-10-27
I would try downloading another liveCD not install CD and retry. I had a similar problem with an Install CD and had to use another one.

---

### Post by ChiefOfSages on 2006-10-27
Okay, I'll download another ISO tonight.  I really hope that's the problem.  I'll post the results later.

I thought all Ubuntu ISOs were both Live CDs and installation CDs.  (On a side note, I also noticed the autorun GUI says 6.06 in its window title.)

---

### Post by vibestriton on 2006-10-27
[https://wiki.ubuntu.com/LaptopTestingTeam/DellInspiron6000](https://wiki.ubuntu.com/LaptopTestingTeam/DellInspiron6000)
Promising.


If you change your mind and decide you don't want to run the LiveCD before install, you can download the alternate i386 version:
[http://releases.ubuntu.com/6.10/](http://releases.ubuntu.com/6.10/)


Given that everything checks out with md5sum, I'm not sure redownloading/burning will help... but stranger things have happened.

Good luck!

---

### Post by ChiefOfSages on 2006-10-28
Thank you for that link.  And I agree, I think it's pretty unlikely that getting another ISO would fix it.  But I'll try it.

When you mentioned installing without the Live CD, that brings me to ask: do you think these errors are only associated with the Live CD?  i.e., will they not be present when using the alternate ISO?  Because I have to reformat before trying and that's a pretty big commitment.

---

### Post by vibestriton on 2006-10-28
Do you have to format your entire disc?  The install options will generally allow you to resize existing partitions. If resizing is supported for your existing fs type(s) and your harddrive has enough free space for a test install (5Gb is more than enough), your leap of faith isn't so extreme.

As far as judging whether or not the same errors will occur when using the alternate CD?  I really don't know but, given your description of the problem, I wouldn't be supprised if the alternate CD allows you to bypass the issue.

Best of luck!

---

### Post by tedrogers on 2006-10-28
Can you buy a small 10Gb HD from the popular auction site and use that just for testing. Should cost no more than a few quid/bucks.

I had problems on my laptop with Live DVD, it turned out that the data was so tightly packed that my old DVDROM was incapapable of reading it. CD's worked ok though, but I still had to do a safemode install instead of Live.

---

### Post by ChiefOfSages on 2006-10-29
Re: vibestriton, I happened to decide my drive was getting too messy right when Edgy was on the horizon, and I wanted to give Linux a try.  So I waited a whole month. :-)  So the reformat was my reason for wanting Ubuntu.

But most importantly, you were right!  The alternate install CD worked like a charm.  Great idea!  Thanks.

Re: tedrogers, I actually tried using the Live CD on two other computers, with mixed results.  Worked on a Dell desktop, and bombed on a Compaq laptop.  But now that I have Ubuntu up and running, who cares! :-)

---

