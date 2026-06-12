---
title: "Possible issue with the install process for Ubuntu Desktop"
date: 2014-07-26
forum: Installation &amp; Upgrades
---

### Post by Eamon_White on 2014-07-26
Hello all,

I would like to share an experience I had trying to install Ubuntu onto my friend's 32 GB USB drive - a bootable version, so that he could plug it in whenever he needs to use it, and have a fully functional version of Ubuntu on his USB stick. A few questions I have before I get into explaining what happened are:

This is possible right? I have installed Ubuntu Live USB before, so that I can boot from it, and get to the menu that says, "Try without installing," "Install," "OEM Install," and one other option that I can't remember off the top of my head. But I have never tried to make my USB stick act as if it were an internal drive on boot (per-say). By this I mean, that I have never tried to partition the USB stick with swap and / so that it would boot properly on its own as a fully installed version of Ubuntu. Just want to make sure that this is possible, and there isn't some problem with doing this on the conceptual level that I am unaware of.

The next question I have pertains to my friends hardware. He has a very new Macbook Pro running a SSD. I knew going into the install that it might be possible that this cause complications (as it is a new technology), but I also thought about how most major servers have probably gone the way of SSD right now...and a bunch of those major servers probably run Ubuntu Server - so Ubuntu Server must work with SSD...so why wouldn't Ubuntu Desktop? (Anyway...that was my logic). So while this was a question I had, I also thought I had figured it out. Also - I'm not sure the fact that he has an SSD would even matter if I am trying to run everything off of his USB stick...but not sure.

Now...to get into the problem.

We dd'd the disk image onto his USB drive (as instructed by the "How to make a bootable USB stick" instructions from the "Install Ubuntu from Mac" page)...and all of that went fine. The problem (gripe) I have with what happened is this:

1. We selected "Install Ubuntu" after booting from the USB drive.
2. We went through any necessary configuration (WiFi, maybe something else) without a hitch.
3. Upon reaching the part of the install that was supposed to be for partitioning, I remember it happening exactly like this:

There was a scan that happened, it said that it was looking for ANY OS that was installed on whatever drive it was looking at. Here in lies the major issue. A.) I was not able to see what drive it was scanning, and B.) It didn't tell me at the end of the scan what drive it had searched, it just said that it didn't find anything (as in NOTHING AT ALL - no OS...however, my friend definitely had a fully functional Mac partition set up prior to the install process). At this point, and I realize this - I should have double checked somehow to make sure the installer was looking at the USB drive when it scanned...as it wouldn't have found anything on that because it was blank - and that made sense to me.

Also...if the installer was searching the primary internal hard drive of the Mac - I may know why it reported that it didn't find anything - because my friend had the whole thing encrypted...however - I find it hard to believe that a hard drive that is encrypted on a low level is flat out undetectable (in the context of installing an OS). If it is the case that, by nature, the encryption was so good that the installer can't even see it - it would be surprising to me that this is possible...however, if it is...+1 to the encryption guys...and +1 to the guy who makes me aware of that fact (so that this never happens again).

Anyway - after the scan - it reported back that it didn't find anything...so I thought it was looking at the USB drive during the scan...and that all was well. The next window had a few options like this:

1. New Install (can't remember exactly what it said)
2. Encrypt
3. LVM

4. "Something else"

Ok...first of all, you should never use the term "Something else" on a menu that is as important as this one (the partition setup) for the obvious reason that you could lose all of your data if you make a mistake (this is what happened to my friend, and why I am kind of annoyed). "Something else" should be renamed to "Manual Install," or something like that on the next version. Secondly, I redid the entire process explained above...after I was able to get his Mac up and running again - because I wanted to see where I had gone wrong...and the second time I went through the process, instead of "New Install" for option 1 (above) - it was "Replace Mac OS". So it found the new OS I had just installed as it should have the first time. I am thinking it worked the second time, because we reformatted the internal hard drive...and we didn't do any low level encryption...so that wasn't an issue (just my theory). Also, although I am slightly guilty of rushing through the install process...I think I would have noticed if the 1st option of that menu said "Overwrite OS" the first time - as it did the second. I don't think it did, I am not 100% - but I am 100% that the installer reported back the first time (after the scan) that it didn't find anything on the drive to worry about overwriting...so if that is what happened...that would also be a major discrepancy that needs to be fixed.

All in all...at NO POINT did it ever warn me that I might be erasing data...the only real warning it seems that you get is, in the beginning of the partition steps, it tells you that you should probably back things up...but as I thought I knew what I was doing (and this wouldn't have happened if I had just been able to see a partition map the first time by default) - I wasn't too worried about deleting all my friend's stuff...apparently...I should have been.

Ultimately, does anyone have any idea what really happened (I think I am correct with a few of my assumptions above, but definitely not sure)? It at least seems to me that the install process for Ubuntu messed up in a major way when it did the OS scan without telling me what drive it was searching, during, or after.

---

### Post by bapoumba on 2014-07-26
There is an ongoing bug (please see the link in my sig) about the wording in the installer. Yes, "do something else" brings you to manual partitioning where you get to see all the actual partitions on the drive, yes other choices may erase everything without warning.

---

