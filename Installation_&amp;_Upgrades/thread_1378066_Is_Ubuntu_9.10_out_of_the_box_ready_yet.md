---
title: "Is Ubuntu 9.10 out of the box ready yet?"
date: 2010-01-11
forum: Installation &amp; Upgrades
---

### Post by houseworkshy on 2010-01-11
Please forgive the verbose mode, bit of a story this one.

I have a machine with two hard drives in it.  One is where I do most of my working and playing and has Ubuntu on it the other is mainly for storing things though, as it is a fair sized drive, has Kubuntu on it as a backup system and for the occasional application which prefers it.  The working drive currently has Ubuntu 8.04lts because I had a lot of problems with 9.10.  Turns out that the main one was to do with my on-board nvidia and after a few days of banging my head against it and a lot of help from this forum (thanks), [www.ubuntugeek.com](www.ubuntugeek.com) , and Puppy Linux (which allowed me to browse for advice without destroying my eyes, prove that I hadn't fried my hardware and let me back my work up to the only CD/DVD writer the machine has in it......very handy thing to have lying around for emergencies is Puppy) was almost sorted out.  Only almost because though I got  my resolution back the refresh rate remained achingly dreadful which, after more formats and installs than I've ever done before ( dozens ) of almost everything else I could find, forced me back to vista for a while.

Eventually, and sorry too dazed at the time to remember how but by then, as Chandler once phrased it I'd already climbed the walls and was gnawing my way across the ceiling, I managed to get the 1024 resolution at 56hz, not good, as it had been at 72 but for very short periods of time, like when I was in Ubuntu trying out the fixes I'd trawled for using Puppy ( at 75hz ), I could at least get in.   Other problems remained however such as continual crash reports, which according to the feedback from bug report feature is common, and the grub beta messing up my other drive too.  

Now comes the part I find strangest, the problems seemed to be inherited.  To clarify: after a lot of unsuccessful palaver, I ended up not only formatting both drives but using dban, a drive wiper, to zero them and prior to that using smem, a ram wiper.  Then putting earlier versions of Ubuntu, 8.04lts, which had previously been fine on what was supposedly a clean system without any remnants.  It didn't take me back to where I'd happily been before 9.10.  If it hadn't been for Puppy and Vista being able to run the monitor properly I'd have assumed hardware failure.

Well that was that.  I have problems with my eyes anyway and they just couldn't take any more of it.  So I got a low end LCD monitor, which I couldn't really afford but my eyes, in combination with my other serious infirmity, an addiction to writing, simply couldn't do without.   With what I'd learned during the above saga I got it to sort of work fairly quickly.  Both resolution and refresh are fine, a blessed relief.

You've guessed that's not all I expect.  Correct.  I put the Kubuntu 8.04 on the storage drive first, it only refreshed at 50hz so, meaning to replace it with K9.04, I put K9.10 on by mistake, a friend had called and I was distracted.  Happily, apart from a cups error during the install, which shouldn't matter, as I shall be printing from the other drive anyway, it seems to work rather well.  The software sources problem has been fixed...cool.  Still leary of the 9.10 GNOME I put the 8.04 on the working drive and that worked too.  There are only a few problems left.  Two concern video.  I get stalls during playback in all the players I've tried and the libdvd css only works during the session I install it in, if I reboot or even leave the machine for an hour or two it forgets all about it and won't play encrypted dvd's anymore until I install again; this is true for both drives.  This is a bit odd as before 9.10 existed all previous versions of Ubuntu didn't have this problem and now they do. The other is obvious, not a fault of the system at all but my own silliness and I know exactly what to do about  it.  8.04's exe3 won't mount exe4 discs, works the other way around of course.  So if you have a fix for the video that would be nice but I can live with it.  

What I'd like to know is; is Ubuntu 9.10 out of the box ready yet?  By that I mean can I just put it in, add the hardware drivers, restricted extras, mediabuntu repositories, install a few bits and bobs, fiddle the GUI the way I like it and that's it, one hour tops.  7.04, 7.10, 8.04 were all like that, and I loved them for it, then something happened and 8.10 and 9.04 weren't; one was display problems after changing resolution and the other was screwed up key mapping.  And then 9.10.  It has been to Ubuntu, for this non programming application user anyway, what ME and Vista were to Windows.  Install and then spend hours researching and doing things to fix it up.  I await 10.04 with some trepidation.  Meanwhile is putting 9.10 GNOME on the working drive so I can dump things in the KDE storage one quickly without rebooting a good or a bad idea for someone who just wants to get on with things other than fiddling with my system?

---

### Post by running_rabbit07 on 2010-01-11
The only way to find out is to run the LiveCD at a minimum. If it works, go for it. I have confidence in it, but I am one in the lucky crown that has all supported hardware froom the get go. 

If you would like to list your system specs to make it easy to compare, I am sure someone with an equivalent system will chime in.

Lenovo 3000 J Series
AMD 64 +3800 X2
2G RAM
NVIDIA Grphics

---

### Post by houseworkshy on 2010-01-11
Thanks for replying
I did test the cd running live,freshly downloaded and burned this morning, and got the usual crash reports.  I was hopeing that the updates would sort it out when it was on a writeable drive.
The basic specs are
AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
GeForce 6150SE nForce 430  which is onboard
And it's an ASUS board and bios

---

### Post by running_rabbit07 on 2010-01-11
With those specs you should be good to go, but give some time for others to chime in if ya want. There has been 3 kernel upgrades from the LiveCD image, so it is harder to tell what will happen.

---

### Post by houseworkshy on 2010-01-11
Cheers I'll hang fire for a while tben give it a go before I put my work back on and get on with things.  Video would be pleasant but I suppose it's a distraction really and maybe something is trying to tell me something. Thanks again.

---

### Post by houseworkshy on 2010-01-12
I've just had a look at the launchpad and it looks like the crash reports I'm getting "EDAC amd64: WARNING: ECC is NOT currently enabled by the BIOS. Module will NOT be loaded." reflects a bug which has not been fixed.  I've only skimmed through so as I'm running form the live disto now and despite being in the correct resolution have a very wobbly graphics.  From the little I have read either it doesn't matter or it can cause instability ( ? ).So as I don't know and have things to do I'll stick with 8.04lts as my working drive for now and look again in a week or so when I have some time.  When it is reported as fixed I'll try it out and if it works will come back and say so.  tc

---

### Post by houseworkshy on 2010-01-16
Well it's the weekend again so I tried.  Clean install from a freshly downloaded CD and still have the crash reports even after updating.  So if one is considering updating to Karmic take a look at this first [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/422536](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/422536) to see how it might affect you before jumping in.  It looks like, with my system, I may simply be one of the few.  I'm still reading up on it and, so far, don't know how serious it is, or even if it is serious;  could be that a harmless little red decoration lives at the top of my screen until it is fixed. I don't know enough yet.  I have a day or so to throw at it and if I can't sort things out still have many older versions lying around on CD so if it is a problem I can simply go retrograde again.  I also have an older machine which is only a memory stick away, if I can get ddr1, from being happy with Ubuntu so maybe I'll save up for one and use that for the bleeding edge stuff and bung something like Lenny on this one for work.   On the plus side the default hardware driver for on-board graphics (nvidia) has worked without any fuss, so that one has been fixed.  
I may have spoken too soon, while I was posting I didn't get any error reports at all.  Looks like the updates may have done it but just took time to kick in.  If when I've tried the various apps and rebooted a few times they don't reapear I'll pop back and mark this thread solved. Cool, Ubuntu is my favorite and I do want to stay with it.

---

### Post by KrazyPenguin on 2010-01-16
The fastest way to set up all that stuff would be by using Linuxmint, which is Ubuntu.

Another way that is easy is to install 9.10 and then install Ubuntu Tweak, and just click click click and set it up the way you want.

good luck!!

---

### Post by KrazyPenguin on 2010-01-16
If your having problems with the installation you might want to try 10.04.
It is in developement, but the newer kernel may help, just to see, not to use as production. 
;-)
(even though I am using it as production right now!!!)
LOL

---

### Post by houseworkshy on 2010-01-17
All's well bar sticky videos which has been true, on my machine, for all versions of Ubuntu since 8.04 for a couple of months now and I can live with that.

---

