---
title: "install probs from cd&amp;usb any ideas??"
date: 2012-07-06
forum: Installation &amp; Upgrades
---

### Post by tommyguns on 2012-07-06
Hi, My E-system 1201 running vista recently developed problems, my recovery disks said it was a corrupted boot manager issue & after a few steps failed the remaining option was a 'destructive recovery'. That process failed at the same point 3 times reporting that the recovery image was missing. The people who sold me the pc said I would need to buy a new copy of windows off them, which I wasn't happy with, given that if computers still included windows OS disks I could have fixed the problem without extra cost.
 
 
Anyway I remembered Linux and thought I would switch over, I saw a few sources that said Ubuntu worked on the widest range of hardware and had the easiest install. My e-system puts up a screen which allows you to load up bios or boot order and then if nothing is pressed moves on to trying to boot from HD. Because of the failed recovery disks it's now unable to boot into windows at all. The pc I'm using to type this is a friends. Before burning my ubuntu cd I checked the md5sum & that was fine i'm trying to install 12.04 32bit. When I put the cd into my e-sys it comes up with
 
 
Loading bootlogo.......
 
 
And sticks there, I've left it for some time but nothing else happens. I tried the cd in my friends pc while windows was loaded and the ubuntu logo came up, I ejected it at that point. When trying the usb on my esys I ensured that usb options were ahead of cd and hd in the boot order....but it would simply freeze up at the point where the sys would give the option to bring up bios and would not move from there or actually load bios with the usb in the machine.
 
Could the state the failed destructive recovery left the HD in be the problem? I'm guessing at the stage it failed, my data was wiped but fragments of vista may remain in other words it is not cleanly formatted.
 
I'm massively frustrated at this point. Could it be a problem due to compatibility with the latest version of ubuntu, do people think an older version may work?
 
I'm just reaching and guessing at this point.

---

### Post by darkod on 2012-07-06
A failed restore could leave the disk with a messed up partition table, but in most cases when booting from cd or usb this shouldn't matter. Hell, you should be able to boot with your cd even with no hdd in the machine. :)

Having said that, some computers can be stubborn if they can't see a valid hdd.

Few options:
1. Take the hdd out (if possible), connect it to a friend's PC and format it. Just to rule it out. If you can't do this, you can at least unplug the hdd and try to boot the cd, just to see how it goes.

2. You said you checked the md5sums of the downloaded image but the cd burning speed also matters. I would burn another cd not faster than 8x or 10x. Then try to boot with it, both ways, by bringing the boot menu if there is one, and by going into BIOS and setting cd-rom ahead of hdd in boot devices.

3. Use your imagination. :) We maybe forgot something, you might think of it looking at your machine. Mostly, play around with the boot options, and creating new cd on lower speed.

---

### Post by oldfred on 2012-07-06
Welcome to the forums.

In addition to Darko's suggestions.

Do you get the two tiny icons at the bottom of the screen as soon as it starts. That is telling you to hit any key to get a screen with some options. Sometime added boot parameters often video realated are required.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by tommyguns on 2012-07-06
You hit on my line of thinking darkrod....I know it shouldn't matter about the state of the HDD when booting from cd or usb but as you said some systems can be stubborn when it comes to the HDD being present and in decent order.  I've never formatted a HDD by removing it and hooking it up to another pc but I'll check out the process online.  I may see about finding a decent bootable DOS program for my usb first, should be able to format the HDD using such a thing if I can track one down.
 
Before I got the laptop I had a desktop, one time when windows became corrupted on that It wouldn't allow the OS disk to reinstall windows, only after formatting the HDD with a dos startup disk was I able to reinstall the system.  Strange....but that's why I considered the state of my hard disk as a possible reason for the problem.  One way or another I'll give formatting the HDD a try.
 
Sorry I forgot to mention the burning speed in my post, I burned it at 10x which was the lowest speed possible on the pc I'm using.
 
 
Oldfred.......No I didn't get any icons.  The system starts, the screen showing to press f2 for bios or f12 for boot options comes on & a bar at the bottom of the screen fills after a few seconds unless either f key is pressed, then the screen goes black and 
 
Loading bootlogo......
 
Appears & that's as far as it get's.  I'll see about getting the HDD formatted and then give the cd another try, see if we get any further.
 
Thank you both for the suggestions

---

### Post by oldfred on 2012-07-06
Unless you changed BIOS to boot CD first it will default to hard drive. Use f12 and select CD. Some systems require both BIOS change and then f12 to boot CD.

---

### Post by tommyguns on 2012-07-06
First off thank you to darkrod and oldfred for replying.
 
 
Also a big thank you to ubuntu for giving me my laptop back......because YES I have finally gotten it installed!!!!! :guitar:
 
 
Here's what I did & I don't know whether it was one thing or a combination of things but I'm just happy it worked & I've gotten my laptop up and running again after vista became corrupted and the 'recovery' cd's that my system created turned out to be pretty much useless & all the manufacturer suggested was that I spend more money to buy a new copy of windows.
 
I entered bios and returned settings to default
 
The first time I tried installing from usb I used _usb creator_ & the iso that I downloaded directly from ubuntu's site. This time I tried **Unetbootin** instead and I downloaded a new iso through that program.
 
And it worked, I wasn't expecting it to so I was surprised and pretty damn chuffed when the unetbootin options screen popped up & the installation ran smoothly. I reset my machine and unplugged the usb and then rebooted & it loaded up the OS fine.
 
So I didn't get any joy at all from trying to install with a cd, despite verifying the md5sum and burning at the lowest speed I could which was 10x. Tried that method with a couple of burned cd's and got no further than: loading bootlogo........
 
Just decided to try with unetbootin as oppose to usb creator on a whim, but I'd certainly recommend using **unetbootin** out of the two & If people have had trouble installing from cd then give the usb installation a try.
 
 
Hope this might be of help to others. Just need to get used to the world of linux now ;)

---

