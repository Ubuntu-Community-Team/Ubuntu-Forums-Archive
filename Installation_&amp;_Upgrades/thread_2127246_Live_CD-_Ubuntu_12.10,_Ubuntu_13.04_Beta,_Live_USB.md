---
title: "Live CD- Ubuntu 12.10, Ubuntu 13.04 Beta, Live USB Ubuntu 12.10- all fail to install"
date: 2013-03-19
forum: Installation &amp; Upgrades
---

### Post by pallath on 2013-03-19
Hey guys!
I hope you'll be able to help me solve this problem.

1) I had Ubuntu 12.10 installed on my PC, but after I did an upgrade through the PPA repository, I messed up a lot of stuff, and I decided to re-install Ubuntu.

2) Live USB refused to boot.

3) Then I used a Live CD of Ubuntu 12.10. Here's where the problems started. The installer crashed repeatedly, and could never complete the installation. Many a times, the Live CD did not boot, and a message came up saying- 'Fatal Error: reverted to Text Mode' (something of that sort).

4) Same problem occurred with Live CD of Ubuntu 13.04 Beta 1.

5) On using the desktop directly through the Live CD, multiple crashes occurred, and before I could even reach GParted, the Live CD crashed, and i was forced to reboot.

I have gone through the same process many times- and I wonder what the problem is.

I even used a external CD drive, and encountered the same problems again.

My PC Config is:-

Intel Core 2 Duo 4400 @ 2.00 GHz
Intel 82945G Express Chipset
160 GB Seagate Barracuda HDD
3 GB RAM (By the way, my RAM was recently encountering problems- I fixed the issue just yesterday.)

PLEASE HELP!!!
:confused::mad::confused::mad::confused::mad::confused::mad:

---

### Post by pallath on 2013-03-19
Note: Tried using a Fedora LiveCD to see if it works.

It starts up fine, I can use the LiveCD, but when I start the installation, a black screen appears saying:-
'Kernel Error- Terminating Anaconda' (Anaconda is the installer for Fedora).

Perplexing....

---

### Post by Bashing-om on 2013-03-19
pallath; Hi !

I might be blowing smoke, but;
1. Is UEFI enabled in bios ( new enough that UEFI is a factor ?)
2. Are you changing the boot priority in bios, to boot the alternate as 1st priority ?
3. Have you checked the md5sum of the install cd ?
4. Did you verify the install's disk filesystem integrity ?

So far as I know, if all the above is verified, should boot !

---

### Post by sanderj on 2013-03-19
> **pallath said:**
> 
3 GB RAM (By the way, my RAM was recently encountering problems- I fixed the issue just yesterday.)


Can you run memtest86? I expect it to be in the boot menu of a live CD. And otherwise it is in the boot menu of Ubuntu installed on your harddisk.

---

### Post by pallath on 2013-03-20
Hi sanderj!

Well, I'm running Memtest86 on my PC now, and it seems to be throwing up quite a few errors.
The test is still going on, I'll post a few pictures of the Memtest screen after a while.

---

### Post by pallath on 2013-03-20
Hell! this is horrible! Memtest is just throwing up so many errors, my screen is scrolling through a list continuously!
Error count is now around 50,000
Edit: 120,000 errors.
Edit: 250,000 errors

Note: Failing Test 5 and Test 7

---

### Post by pallath on 2013-03-20
OK, the errors are appearing first in _Test #5, Pass 0_ (**~220 errors**), and now in _Test #7, Pass 0_ (**now around 550,000 errors**)

I'm gonna try to find out which module is faulty by sunning memtest using only one RAM module at a time (first the 1gb ram, and then the 2gb ram)

Thanks for the instructions guys!

---

### Post by Redalien0304 on 2013-03-20
sounds like to me it means Possibly a Bad Memory stick do 1 memory stick at time if you can

---

### Post by pallath on 2013-03-20
Thanks alien0304!

Here's what I did-

1) I tried Memtest with the 1 GB Mem stick in Slot- 1
 Result: COMPLETE fail in Test #7

2) I then tried Memtest with the same Mem-stick in Slot- 2
 Result: Complete fail in Test #7

3) After that, I tried Memtest with the 2 GB Mem-stick in Slot-1
 Result: Same

4) Now, I'm trying Memtest with the 2 GB Mem-stick in Slot-2
 Result: Yup, the same scrolling errors in Test #7

Could it be the Motherboard that's gone, or something?

---

### Post by sanderj on 2013-03-20
> **pallath said:**
> Thanks alien0304!

Here's what I did-

1) I tried Memtest with the 1 GB Mem stick in Slot- 1
 Result: COMPLETE fail in Test #7

2) I then tried Memtest with the same Mem-stick in Slot- 2
 Result: Complete fail in Test #7

3) After that, I tried Memtest with the 2 GB Mem-stick in Slot-1
 Result: Same

4) Now, I'm trying Memtest with the 2 GB Mem-stick in Slot-2
 Result: Yup, the same scrolling errors in Test #7

Could it be the Motherboard that's gone, or something?

Yes.
Or: wrong BIOS settings (CAS?)
Or: both memory modules defect

---

### Post by tux-gamer on 2013-03-20
as mention by sanderj, it could be the bios, you could try reset the bios then load default setting and try memtest again.

---

### Post by pallath on 2013-03-20
OK- I've not messed around with the BIOS settings till now, except to change Boot Order to boot LiveCD and USB first.
Note- (My PC is like around 5 yrs old, and has no UEFI)
So I don't think it is the BIOS.

Anyway, maybe I'll follow your advice, and reset the BIOS to default, then try memtest again.

As for the RAM, my 1 GB RAM module is as old as the PC (it was the original RAM module), but I bought the 2 GB RAM module just last year, I think around February 2012.
So it seems less likely that both the modules could have failed at the same time.

---

### Post by Redalien0304 on 2013-03-20
yep maybe Motherboard also Look for Blown Caps on motherboard. If caps are Flat there Ok if there Bulging on top there Blown Kinda like a Bulging Balloon on Top Cap.

---

### Post by tux-gamer on 2013-03-21
could be PSU too, if the PSU cannot supply the motherboard and other hardware inside the computer, it can make system not stable.
modern bios can show voltage value, try check it too in your bios.

---

### Post by pallath on 2013-03-22
Ok guys... I'll try it out.. I'll look at the motherboard and post the result.

---

### Post by pallath on 2013-03-22
OK... I finally succeded in installing Ubuntu. I did this by using a new 2gb RAM and my old 2gb RAM together. Both the RAMs still threw up errors in Test #7 (memtest86+), but (after nearly 10-15 crashes), I was able to install Ubuntu 12.10.

I dunno.. should I believe the test results that say my RAMs are faulty?

What do the errors in Test #7 (around 2,500,000 errors each time) mean anyway?

Should I attach a couple of images of the screen during memtest86+ ?

---

### Post by sanderj on 2013-03-22
> **pallath said:**
> OK... I finally succeded in installing Ubuntu. I did this by using a new 2gb RAM and my old 2gb RAM together. Both the RAMs still threw up errors in Test #7 (memtest86+), but (after nearly 10-15 crashes), I was able to install Ubuntu 12.10.

I dunno.. should I believe the test results that say my RAMs are faulty?


Depends ... do you want the blue pill, or the red pill?

"The red pill and its opposite, the blue pill, are pop culture symbols representing the choice between the blissful ignorance of illusion (blue) and embracing the sometimes painful truth of reality (red)."

[http://en.wikipedia.org/wiki/Red_pill_and_blue_pill](http://en.wikipedia.org/wiki/Red_pill_and_blue_pill)

---

