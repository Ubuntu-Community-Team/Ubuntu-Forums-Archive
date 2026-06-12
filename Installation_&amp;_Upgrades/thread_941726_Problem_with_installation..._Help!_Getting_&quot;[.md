---
title: "Problem with installation... Help! Getting &quot;[Errno 5] Input/output error&quot;"
date: 2008-10-08
forum: Installation &amp; Upgrades
---

### Post by ImEnigma on 2008-10-08
Well, recently Vista just quit booting one day after I started to Dual Boot it with Xp, then neither of them worked so I called the local computer shop to ask about it and see how much it would cost to be fixed, they told me what they thought COULD have been wrong and said that it would cost between $15 to $125 and I don't have that money on me just to dish out like that, so I got on my brothers computer and burned ubuntu to a disk. Now I'm running the live session, and I really like it, aside from certain text looking like crap and barely being able to read it, it's great! 

But I have one little problem, when I try to install and get through all the steps, I get this error a little bit into the "Installing System" part of the installation:
```
The installer encountered an error copying files to the hard disk:

[Errno 5] Input/output error

This particular error is often due to a faulty CD/DVD disk or drive, or a faulty hard disk. It may help to clean the CD/DVD, to burn the CD/DVD at a lower speed, to clean the CD/DVD drive lens (cleaning kits are often available from electronics suppliers), to check whether the hard disk is old and in need of replacement, or to move the system to a cooler environment.
```

I've reburned the disk like 3 times, My room is really not hot AT ALL and my computer isn't even a year old so the drive should be perfect... I've never had any problems before, I've also burned at the lowest speed possible with the program I'm using (PowerISO), which is 4x, the guy at the computer store said that .iso's arn't very friendly either, and that they tend to leave out a few files pretty often... So can anyone help, I really like Ubuntu and would like to use it as a primary operating sstem until I get my other OS fixed. :) 

Help?

---

### Post by Partyboi2 on 2008-10-09
Try booting with noacpi as a boot option. You  can do this by pressing F6 at the main menu and and adding ```
noacpi
``` to the end. Also make sure that your cdrom lens is clean. This error sometimes is a result of a dirty lens.

---

### Post by dci-Japan on 2008-11-05
Installing Ubuntu 8.10 [Errno 5] My Success Story

My solution to [Errno 5] on Ubuntu install was to remove some RAM modules.

I had great trouble installing 8.10 to my computer (model: HP d330). It took me three days and countless hours researching around the internet. Here is my success story.

I downloaded the ISO and attempted to install from the Live CD. The following error appeared at about 24% of install process:

[Errno 5] Input/output error

This particular error is often due to a faulty CD/DVD disk or drive, or a faulty hard disk. It may help to clean the CD/DVD, to burn the CD/DVD at a lower speed, to clean the CD/DVD drive lens (cleaning kits are often available from electronics suppliers), to check whether the hard disk is old and in need of replacement, or to move the system to a cooler environment.

1. Attempted reburn CD-R at slower speed. Same error.
2. Attempted install with "Alternate CD". Same problem (it froze up somewhere in "copy files to disk" process).
3. Attempted boot from Live CD and double click "Install". NO GO. Wouldn't even start process.
4. Repeated all the above in various ways. Same results.
5. Tried changing the various choices under F6 on boot-up. Freeze or same error. 
6. Live CD then begin to hang on boot from CD. Couldn't get anything to do anything.
7. Attempted to install from Flash card (using separate PC to set it up). Booted fine, but same error on install.
8. Attempted many solutions offered on various forums online. Still no luck.
9. Tried noapic options and others to no avail.
10. Tried repartitioning hard drive, and wiping hard drive and etc. etc. etc.
11.Gave up and installed Windows XP. Hated it (as usual). Waited several hours. Kept repeating all the above plus anything I could think of. Redownload ISO. Burn at slower speeds. Try Alternate CD. Try Flash card again. NO LUCK. Fiddle with various settings again.

And then I used the little grey cells in my head (as Poirot would say in an Agatha Christie novel). I remembered someone somewhere suggested RAM error as the culprit. I ran the memory test without a problem (that took many hours!), but still I was supicious about the memory. My PC has four memory slots but with 3 actually memory sticks. 256Mb (original memory stick that came with computer) + 1Gb (cheap no brand stick added later) + 1GB (another added no brand stick). I simply took out the two 1Gb stick and left only the original 256Mb stick and attempted an install. Bang! It worked. No error. No problem (except it was as slow as molassis to install...). After the successful install, I replaced the 2Gb of memory and rebooted. Everything worked out. RAM modules might be faulty but everything seems fine.

I'm not sure if this solution will help everyone. The cause of [Errno 5] might be different for each machine, and sometimes just trying a million attempts leads to an eventual success. But in my case, removing most of the RAM solved the problem. 

Finally I can get on with enjoying Ubuntu 8.10.

---

