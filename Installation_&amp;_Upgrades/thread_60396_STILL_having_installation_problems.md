---
title: "STILL having installation problems"
date: 2005-08-27
forum: Installation &amp; Upgrades
---

### Post by dritchie on 2005-08-27
Trying to install Ubuntu on a "old" HP machine that has a n AMD Athlon 1400 .
The machine[SIZE=3][FONT=Arial Black] now [/SIZE][/FONT] has 240 of ram plus 16 meg for video. (256 total)

Goes thru hardware detection, scan CD-ROM, loading add'l components -
no net config, as I have no network connected to the machine as yet.
Then I am having trouble partitioning the hard drives -
hdo is a 40 gig Samsung 

I have disconnected hd1, which is a 20 gig Maxtor

still get error messages

"attempt to mount a file system on type ext3 in IDE1 slave,
partition #1 (hdb1) at / failed"

I got past that, although I'm not sure how I did it,
I can then get to "installing the Ubuntu base system"

it runs to 6% then the machine "locks up"

in about a dozen tries it stopped at;

6% validating alsa-utils...

6% validating apt...

6% validating aptitude ...

ALWAYS 6%

I can not run the "live CD" on this machine either.

I have tried with any number of ram simms, they can't all be bad.
If the CD were bad, I couldn't run the live CD on this  machine ( I can)

It doesn't seem to care which CD  I  try ... it ALWAYS stops at 6%

Something must be going on at 6% that it doesn't like, what is it ?
Is there a way around it???

Or do I need to go out and find "another" "junk" machine ???

Thanks for any help

Don Ritchie [email]dritchie@dr.com[/email]

---

### Post by dbcoder on 2005-08-27
Could you possibly post what all the major components of your system are?  This will make it easier for myself and anyone else that wishes to help you.  Even though this will most likely not resolve the issue as I think it is a hardware issue, but there can be a chance that some of your hardware isn't supported. 

What it sounds like to me is there is a hard drive failure.


What you should do is find the manufacturer's website and download their diagnostics software.  Run that, and if you check-out 100% alright, then it's improbable that it's a hardware failure.

I can't help you out until you give details :P


Well, I re-read your post.  Since you are having issues with live-cd's it's less probable it will be your hard-drive, yet it can be since your hard drive is mounted.  Make sure your cd's are clean and scratch free, any errors on the cd(s) will most likely end up screwing up installation or installing/loading corrupt data which will cause issues.

---

### Post by dritchie on 2005-08-28
I'm going to try and find another "out of service" computer.
I have been told, just today, that the computer that I am TRYING to load Ubuntu on did have some "lock-up " problems while running XP.
I ran it for three days in XP without any problems, but I wasn't really doing anything.
I am going to "ASSUM" that the problem is the HP Athlon for right now.

Thanks

Don

---

