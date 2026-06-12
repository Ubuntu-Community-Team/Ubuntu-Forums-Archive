---
title: "No sound after upgrading to 9.10, HDA-Intel (NOT a dell laptop)"
date: 2010-01-24
forum: Installation &amp; Upgrades
---

### Post by johnsky on 2010-01-24
Upgraded to 9.10.
No sound. Was working prior to upgrade.

aplay -l
outputs
*aplay: device_list:223: no soundcards found...*

Audio device should be :
[I]00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
	Subsystem: ASUSTeK Computer Inc. Device 82bb
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at f9ff4000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel[/I]

Other threads have suggested running alsamixer manually from terminal, this results with :
*alsamixer: function snd_ctl_open failed for default: No such file or directory*


Attempted the following :
 sudo nano /etc/modules
added snd-hda-intel to the end of the file, saved.

ran alsamixer, again, *alsamixer: function snd_ctl_open failed for default: No such file or directory*

At this point I'm following this guide : [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
Which looking back, I've done what it's asked, continuing on.


The guide has me remove and reinstall ALSA.
*sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils*

then
*sudo apt-get install linux-sound-base alsa-base alsa-utils*

and I also had to reinsall ubuntu-desktop as the ALSA purge removed it for some reason.
*sudo apt-get install gdm ubuntu-desktop*

Then rebooted.
Still no luck, alsamixer still returns the *No such file or directory* error.


The guide is asking now that I compile the ALSA drivers from scratch... which I think is getting a little out of hand and slightly off base.
There MUST be a simple explanation as to why the upgrade from 9.04 to 9.10 has stopped my HDA-Intel sound card from being usable.

There were a few suggestions for Dell laptop users on other threads that have them edit a .conf file and add the model of their dell laptop to the HDA-Intel driver... but I'm not using a dell laptop.

Any help would be greatly appreciated.

---

### Post by johnsky on 2010-01-25
No such luck to have any takers yet?

I'm still searching for a solution to this. I haven't resolved it yet.

I noticed that the HDA-Intel / Upgrade to 9.10 issue has been marked as a bug. If anyone knows of the current workaround, I would greatly appreciate it, or even any information on a timeline to the correction of this bug.

---

### Post by johnsky on 2010-01-27
Still trying...

Just attempted this walkthrough.
[http://ubuntuforums.org/showthread.php?t=1316634](http://ubuntuforums.org/showthread.php?t=1316634)

Not a peep from my sound card.
All levels are set.
aplay -l still returns "No soundcards"

I've tried adding
options snd-hda-intel probe_mask=1 model=asus
options snd-hda-intel probe_mask=1 model=auto
options snd-hda-intel probe_mask=1 model=minimal
and a few others to the end of
/etc/modprobe.d/alsa-base.conf
restarting after trying each one.

Nothing.
I've reinstalled alsa and pulseaudio so many times... it's getting ridiculous.

I've almost had it... I'm thinking of spending a few hours backing everything up, formatting 9.10 off of my machine, and going back to 9.06.

What a mistake upgrading was.

If anyone has any information that can help... anything at all... please, help!
I'm picking up an external drive in a couple of days to move everything and keep a constant backup. It will be at that time that I revert back to 9.06.

At least 9.10 had a nice splash screen...

---

### Post by johnsky on 2010-01-31
Alright. It's done.

Out of curiosity, I burned a new copy of 9.10, sound runs fine with live version of 9.10.

So somehow the upgrade screwed the sound up, but a fresh install works ok.

Formatted, installed 9.10 fresh, everything is fine again.

In the process of moving my files back onto my hard drive.



Hopefully this doesn't happen to too many other people.

---

### Post by anupkhanal34 on 2010-02-06
[FONT=Georgia][SIZE=2][COLOR=Blue]I have a HP Pavilion- dv3 2155mx laptop. 

I also had been using the earlier versions of ubuntu. I updated my system to ubuntu 9.10 and then I started facing a lot of problems. 

First I had no wireless network and no sound. I was so frustrated.

The I checked my System>Administration>Hardware Drivers, there I found out that I had to install one of my hardware drivers, for my HP it was Atheros ... 

I updated my software sources and then insatlled the sound .lib files. For the 1st time I did this my sound worked. Then I made more changes to my ubuntu until I rebooted it. 

But after I reboot the system, I had no sound at all. The touch button on my laptop for the sound was also lighting red all the time. 

I tried everything possible. Add lines into some code files to rebuilding alsa. Nothing worked. 

I re-installed ubuntu 4 times. First two times within windows and later in a new partition in a hope that it might work. 

So, please help me. Any comment from your side will be highly appreciated.

Thankyou in advance.
[/COLOR][/SIZE][/FONT]

---

### Post by kronictokr on 2010-02-14
try this, has various fixes included, works like a charm

[http://swiss.ubuntuforums.org/showthread.php?t=1395089](http://swiss.ubuntuforums.org/showthread.php?t=1395089)

---

### Post by arleben on 2010-02-15
After applying the latest updates that contained the new version 2.6.31-19  I experienced the "no sound" problems on my Gateway laptop. 
On Version 2.6.31-17 (which Rocks), everything worked really good. However, after applying V- 2.6.31-19 there was no sound with any application; including the virtual operating systems running under virtual box,they  couldn't detect a sound device. 
I decided to restart the laptop and went back to Version 2.6.31-17 from the boot menu. Everything went back to normal. I wonder if a driver got removed or updated with the new version.

---

### Post by matthus on 2010-03-12
[https://help.ubuntu.com/community/RestrictedFormats/](https://help.ubuntu.com/community/RestrictedFormats/) 
I have found that the recomended libdvdcss in the above link appears to conflict with sis966 recognition in ubuntu 9.10
try and remove it if you have it installed
it may be that there was one there already of a newer version
I had not tried to play a dvd but was trying to think foward to restricted formats

anyway remove it and see if it works

---

