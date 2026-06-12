---
title: "Ubuntu too slow"
date: 2007-09-11
forum: Installation &amp; Upgrades
---

### Post by mmacintyre on 2007-09-11
I am newbie to linux and ubuntu.  I have installed ubuntu about 5 times on my machine, dual boot with windows XP.  Ubuntu seems to be much slower than using windows, for example firefox is much slower, everything app load time, opening new pages, scrolling has a huge lag time.  Boot time does not seem to be any longer than with Windows.

I would love to be able resolve this issue and I am not sure there are some background processes working that I can't find or something.  My system specs are below maybe there is some hardware that does not work correctly.

Celeron 2.6
RAM: 512mb
HDD: 80 GB
RADEON 9200 SE video

I followed all the standard install instructions and left enough space for the different drives and swap.  Has anyone else experienced similar issues.  It was my understanding that things should be faster with Ubuntu.

thanks for the help in identifying the issue, as I really want to use linux full time but I can't make the jump if it is going to slow me down by this much.

---

### Post by tgalati4 on 2007-09-11
Your observations are correct.  Firefox does run better under Windows than Linux.  Strange but true.  Applications do sometimes take longer to load (initially) under Linux.  Windows does some prefetching to get things to load faster.  You can set up Linux to do the same.  Boot times are similar.  Lagging scrolling could be due to a poor ATI Radeon video driver.  

Search the forums for ATI video drivers and you will find lots of info.

Try this:

Let your machine run for 165 days straight--no rebooting:

Ubuntu 6.06.1: Yes.

Windows: No.

---

### Post by kenji-san on 2007-09-11
[Opera]("http://www.opera.com/") runs much faster and can be more reliable than firefox but it comes down to personal preference.

How much swap space to you have allocated?

---

### Post by FrancoNero on 2007-09-19
I had firefox scrolling/ opening pages go very fast at one point (ubuntu gutys), but that was weeks ago, i was hoping for one of the thousands of updates everyday it would go back to normal again.
also, moving windows around, it's all choppy and slow... not sure where to look for the problem....

---

### Post by n00blet88 on 2007-09-19
ive never had a problem with my ubuntu speeds. i couldnt get it installed on my old dell 2400 its like 5 years old tho. Ubuntu runs like a dream on my new Sony Vaio n11s it has 1 gig ram 1.6ghz intel centrino dual core. but ubuntu is easy to run isint it? so i dont have a clue. htere must be something on google that has commands etc so you can edit registry and stuff

---

### Post by WakkaDojo on 2007-09-19
Ubuntu is much less stress for your system to run. And I mean MUCH less. I think doing word processing in windows can be 5 times as much work as doing the same task in Ubuntu. 

One reason why your computer might seem slow is because Ubuntu ships with a generic kernel, meaning it is designed to run on any x86 processor, meaning it's default to the lowest common denominator. Essentially it's optimized for a pentium 1, maybe pentium 2 (I'm not sure).

Anyway, try compiling a new kernel and see if that helps. I know it did for me (my computer runs much faster since I did so)! There are various tutorials on how to do this, but here's a pretty good one:
[http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

It takes a few hours to compile, but it is absolutely worth it; I'm sure you'll agree if everything goes smoothly.

---

### Post by FrancoNero on 2007-10-07
well, this might be a philosophical standpoint of mine, but I think that, as the end user, I shouldn've have to compile squat ;-) and I won't. what I was saying is, that it worked fine, thena  few updates later it didn't, I guess at some point just something go screwed up. i'll do a fresh install when the final is out, anyways, and i"ll report back on how it's going

---

