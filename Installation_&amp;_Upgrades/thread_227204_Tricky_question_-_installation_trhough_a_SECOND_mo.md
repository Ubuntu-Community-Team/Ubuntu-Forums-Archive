---
title: "Tricky question - installation trhough a SECOND monitor"
date: 2006-08-01
forum: Installation &amp; Upgrades
---

### Post by Tarrasque on 2006-08-01
Yes, that's it.

Unfortunately my laptop has fallen and the LCD monitor is broken near to useless now. :(:(:(

In the best philosophy of Linux being able to take advantage of whatever piece of hardware you have floating 'round the house, I thought of recycling the laptop as a DVD/DivX/media player, by connecting it to my TV and stereo.

Problem is, can I go through the installation process (expecially partitioning, since I have other sensible data on disk) WITHOUT BEING ABLE TO USE THE PRIMATY MONITOR?

Will the second monitor-out port be enabled from the boot-fron-cd installation startup (I think the S-Video out to be enabled is askind too much, but plugging in a standard CRT monitor just for installation will be more than enough)?

Is there any other way to perform an installation without video output?

Don't know, by system beeps, a script file I can edit on another PC... whatever mean that can bring me to the point where I have a video output on a secondary monitor of ANY sort, and then I can go on with installing applications and stuff as usual?

Thank you very much.

---

### Post by orb9220 on 2006-08-01
Well my system has dual monitor setup and install always used the primary  and the secondary was a garbled mess during install until I config the xorg file.

But I stumbled onto the liveCD boot process by selecting the second entry to boot into safe graphics mode and my livecd booted up with clone on BOTH! monitors.

But I do not know if this will stick thru during the install process?

But try it and see Maybe you'll be Lucky.

---

### Post by Tarrasque on 2006-08-03
Live CD?

I didn't know Ubuntu had a Live CD edition. That's nice.

Can I install it permanently on HD after the boot? If I can, is it a full fledged Ubuntu installation (which means that I can install everything I want by just apt_getting applications) or is it a "special" edition?

and... where can I find the Live CD?

Thanks

---

### Post by orb9220 on 2006-08-03
The liveCd runs totally from cd to try out everything, 

If you likey then there is an install icon on the desktop that will let install as dual boot with xp or clean install to linux.

If you install it will let you manually edit partitions for dual boot option.

I have xp on first hd 12gb then a 42GB ext3 partition for / root then a 1 gb for swap. My second 120GB HD is fat32 so that windows and linux can read and write to it.

Works out prety sweet.

---

### Post by orb9220 on 2006-08-03
[http://www.ubuntu.com/download](http://www.ubuntu.com/download)

---

### Post by Tarrasque on 2006-08-03
I found links only to "desktop", "server" and "alternate" derivatives (for tue various architectures).

Is the "desktop edition" working also as a Live CD?

Or is it the "alternate edition"?

---

### Post by orb9220 on 2006-08-03
Desktop is live and I think they are all live.

---

### Post by Tarrasque on 2006-08-03
Thank you very much. :D

Your help has been quick and greatly appreciated.

I'll try the Live Cd as soon as I can download and burn one.

Reading through the docs it seems that I can perform a HD installation even from "Live CD" mode, much like a Knoppix, which, if the Live Ubuntu already has set up my laptop to run with a cloned second monitor pretty much solves my problem.

I'll post the results

---

