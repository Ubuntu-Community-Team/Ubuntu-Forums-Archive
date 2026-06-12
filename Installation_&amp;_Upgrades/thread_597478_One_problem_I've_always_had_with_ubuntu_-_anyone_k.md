---
title: "One problem I've always had with ubuntu - anyone know a fix?"
date: 2007-10-30
forum: Installation &amp; Upgrades
---

### Post by Synth3t1c on 2007-10-30
I've always had this problem with ubuntu. I'd like to start off by saying I've always used fairly low-end Toshiba laptops.

This happened with Dapper and Feisty.

Basically, I'd be running everything ok for a good while. Then, it would say something like disks havent been checked in x amount of restarts, checking disk now.

It always finds errors, and cant fix them, and can't start up ever again (because of the errors, etc).

When I used dapper, it did this after I finished an English paper. Lucky for me, I could grab the paper using the livecd and email it to myself. I formatted, and put XP on it and didnt have problems after that. Now that I think of it, this may have been after I upgraded to Feisty, so Dapper I don't think is the issue.

This summer, I was getting my laptop ready for school. I put Feisty on it again, and used it for about a month with everything PERFECTLY configured (all the programs I want/need, firefox extensions, etc...). 3 days before I leave for school, bam same ****. I didn't have anything I needed on it, so I tried to put XP on it. The hard drive actually died. I replaced the HD, put XP on it, and everything was dandy.

Now, I don't know if it was coincidence or what, but everytime it checks my disks it ***** all my **** up.

I always use the full guided, entire disk partition. Anything I'm doing wrong?
I REALLY want to put Gutsy Gibbon on this laptop with mac4lin. I was also always using Automatix2 - I heard it caused problems, but is that the type of problem it can cause?

Thanks in advance!

sorry for language, i copied and pasted from another forum.  good thing it *'s it out

---

### Post by Herman on 2007-10-30
Hello Synth3t1c,
I am a person who likes to run e2fsck fairly regularly on my file systems and I think it's a good thing to do. 

I'm guessing maybe there might be some physical problem here that is damaging your hard disks. You say this is happening in a laptop.

Is it possible that you might be using the laptop while it is resting on some kind of a soft surface that might be blocking air vent underneath and causing temperature problems in your hard drive?

Another thing, do you ever carry your laptop or move it around at all  while it is still turned on, while the hard disk is still spinning?

When it does run the file system check, and finds errors, mine always says 'Please run e2fsck manually'.
Do you realize there are lots of different options you can run e2fsck with to make it actually repair the file system for you?
If you aren't good with the command line, you can use GParted in Gutsy to check your file system, and that has good repair options and is easy for anyone to use. Try that, that should fix it. 
Regardless of whether you choose to run a file system check from the command line or use GParted, you should do so from a live CD on an unmounted file system.

Regards, Herman  :)

---

