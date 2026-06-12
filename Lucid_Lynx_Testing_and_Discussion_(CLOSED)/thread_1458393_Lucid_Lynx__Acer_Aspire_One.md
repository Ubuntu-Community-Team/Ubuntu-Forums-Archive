---
title: "Lucid Lynx / Acer Aspire One"
date: 2010-04-19
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Ibidem on 2010-04-19
Well, other people have posted little bits about how Lucid is doing on their Aspire One, but there appears to be no "official thread" for all versions yet...which I hereby attempt to rectify.
I can provide info on the AOA 150 (aka "zg5", Windows version).
Appears to work largely.

Ethernet (Realtek 8102E/r8169):  Works perfectly, out-of-box.
Wireless (AR5007/ath5k/madwifi-hal):  Works with ath5k, but does drop connections (to the point of sometimes being unable to do large updates); install madwifi instead for improved connections (I compiled the Feb. snapshot for madwifi-hal, which works very well but slightly lower signal strength is reported); must do some workarounds for hibernate.
Graphics (Intel 945GME/i915)  Decent here; flash is decent, Compiz/clutter not tested, xcompmgr slows things down; glxgears ~1150 frames/5s
No 32bit color support, that takes a "generic" driver (?!?)
Webcam: works OOB, xorg v4l contains the driver...sucks the battery, even if driver isn't loaded.
Flash card readers: NOT TESTED!  Right should work with latest bios; there are also a couple workarounds.
Audio-works.
Battery life: bearable after tweaks (reports ~ 2:45, but that is just a rough idea); default is way too low (don't remember for sure, but it was under 2 hrs. IIRC)
Boot-I get ~25 seconds; grub1 is much faster than grub2, but the latter has 915resolution available as a module (for those who need it)...

Please post, especially if you've got another model like the 532 or 731; if anyone has the ssd version, info would be interesting.

---

### Post by blazemore on 2010-04-20
> **Ibidem said:**
> Well, other people have posted little bits about how Lucid is doing on their Aspire One, but there appears to be no "official thread" for all versions yet...which I hereby attempt to rectify.
I can provide info on the AOA 150 (aka "zg5", Windows version).
Appears to work largely.

Ethernet (Realtek 8102E/r8169):  Works perfectly, out-of-box.
Wireless (AR5007/ath5k/madwifi-hal):  Works with ath5k, but does drop connections (to the point of sometimes being unable to do large updates); install madwifi instead for improved connections (I compiled the Feb. snapshot for madwifi-hal, which works very well but slightly lower signal strength is reported); must do some workarounds for hibernate.
Graphics (Intel 945GME/i915)  Decent here; flash is decent, Compiz/clutter not tested, xcompmgr slows things down; glxgears ~1150 frames/5s
No 32bit color support, that takes a "generic" driver (?!?)
Webcam: works OOB, xorg v4l contains the driver...sucks the battery, even if driver isn't loaded.
Flash card readers: NOT TESTED!  Right should work with latest bios; there are also a couple workarounds.
Audio-works.
Battery life: bearable after tweaks (reports ~ 2:45, but that is just a rough idea); default is way too low (don't remember for sure, but it was under 2 hrs. IIRC)
Boot-I get ~25 seconds; grub1 is much faster than grub2, but the latter has 915resolution available as a module (for those who need it)...

Please post, especially if you've got another model like the 532 or 731; if anyone has the ssd version, info would be interesting.

Unusably slow on the SSD version, with whatever tweaks I attempted to use (including using ext2)

---

### Post by hajk on 2010-04-20
> **blazemore said:**
> Unusably slow on the SSD version, with whatever tweaks I attempted to use (including using ext2)
That's why I replaced the SSD on my AAO with a Samsung 40GB HD... now it's a snappy little travel companion.

---

### Post by bailout on 2010-04-20
Interesting to hear your experiences. I have the AAO 150 (ZG5) as well but haven't tried Lucid yet. I currently have karmic ubuntu/kubuntu and a minimal xfce install to assess whether there is any real difference in memory usage and power between them.

Could I just ask you a question on heat. I have the linux model that came with 512Mb ram and a 160gb hd. I have added another 1GB ram. I have enabled acerhdf but I am still finding that the fan comes on a lot. I have set the acerhdf to come on at 60 and off at 55. I ahave been using it in a cool room, 16 C, and find that just browsing with Opera the fan comes on after about 20-25 min. After the fan turns off there ia only about 3-4 mins before it comes on again. 

Without acerhdf the fan soon comes on and stays on. With acerhdf I get that short initial phase while it heats up but then it is just constant on/off from the fan every few minutes. I don't know which is worse tbh ;)

Do you get similar performance? I don't know whether how mine performs is normal or whether there is something wrong with it. I am thinking of taking out the extra ram as that takes extra power and will hence produce more heat.

---

### Post by celticbhoy on 2010-04-20
I have a ZG5 also, and have had Lucid on a partition since the start. The wifi is without a doubt the biggest problem, especially when my desktop is also on for some reason. My boot times usually skirt around 40-45 seconds using Grub 2 (burg), but I think another reason for the slowish startup is that the hard drive is partitioned with four other OS's, that said apart from the Moblin Remix, lucid starts quicker than the rest. Compiz works fine, but there were a few times I had to use fusion-icon to get it started (compiz is usually not on, to keep a tab on the startup time). As for the card readers, From the start I have used the pciehp workaround.

Oh and no issues with the battery, as mine is goosed....

---

### Post by DavidOC on 2010-04-20
I've an AOA150 here and I have the same problems here.  The connection dropouts are very frustrating.  Sometimes the connection drops every few minutes, especially when using bandwidth intensive applications.

On a full charge, I get around 2 to 2 and a half hours battery life with my 3 cell battery, which I think isn't bad.

---

### Post by Ibidem on 2010-04-20
@bailout:
Fan is similar here, but I set fanon around 63 degrees--much more time between off and on.
I don't get the fan started, if I'm not online/playing with a heavy program (GIMP, GRASS).
@celticbhoy:
I have so many os's I need to count them...
Lucid, Kuki, XP (sda2), FreeDOS(sda3), Nimblex (sda2/lives w/ XP), Scientific Linux (in extended partition somewhere), TCL=7 OS's
Lucid is on sda13--So I should have worse performance on boot.
But IceWM+PCManFM is 3-5 seconds after login...

Enabling madwifi solved wireless issues for me (apart from rare glitches that might be anything).

---

### Post by elmago79 on 2010-04-21
> **DavidOC said:**
> I've an AOA150 here and I have the same problems here.  The connection dropouts are very frustrating.  Sometimes the connection drops every few minutes, especially when using bandwidth intensive applications.


Weird. It seems I'm the only one with a AOA150 that doesn't have any trouble with wifi whatsoever.

Has anyone tried the card readers without the pciehp workaround? Are they ever going to work out of the box?

I'm using a different method for enabling the card readers since 9.10 ([here]("http://blog.liberailvoip.it/2009/10/23/acer-aspire-one-karmic-koala-9-10-anteprima-ottimizzazioni/")) and it works fine for me.

---

### Post by DavidOC on 2010-04-21
I've compiled and installed the latest madwifi snapshot, but if I blacklist the ath5k modules and restart I'm not able to use the wireless.

Can anyone help me with this?

---

### Post by travy4911 on 2010-04-21
This is going to sound weird..I have a AAO 150 that doesn't have any problems listed here with the exception of the fan running all the time.  That's an easy fix however.  It Seems that every AAO 150 user has different experiences with it.  Weird?!?!

---

### Post by Ibidem on 2010-04-21
The madwifi modules are blacklisted at install.
You will need to comment that out (or use jockey-gtk)
Also, at least if you use wicd, you will need to switch the wireless device to ath0 (Wicd->Preferences button->General Settings tab)

The wireless problems w/ ath5k took a while to show up, then hit full force for me.

---

### Post by Lucretius on 2010-04-21
running netbook remix here

no issues other than flash can be slow at times.

I gave up on the atheros wireless card (I believe the problems with it are hardware related)

I have since swapped in an intel wireless card and never had one single problem

---

### Post by Ibidem on 2010-04-21
Atheros drivers are either part proprietary (madwifi) or partly reverse-engineered (ath5k).  Not sure exactly what the scoop is on madwifi-hal, but AR5007 chips are among the "least supported" Atheros ones around...
But it does work with madwifi-hal.  

Intel chips have one, open source, driver--in the mainstream kernel.

---

### Post by oubiwann on 2010-04-23
I've got an Acer Aspire One D150-1920. It was running Lucid Alpha just great. After I upgraded to one of the betas a few weeks ago, the trackpad completely stopped working (yes, I've tried the fn f7 trick). I filed this bug about it:

  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/542848](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/542848)

Yesterday when I upgraded to the latest packages the keyboard crapped out. Now the only way I can log in is by using a USB keyboard and a USB mouse. After logging in, I found that the wireless card was no longer working either. Once I'd scrounged up a keyboard, I logged in and did an apt-get update and apt-get upgrade and 78MB and a reboot later... everything works! Even the trackpad! :)

I'm pretty happy about that. Go Kernel team!!

---

### Post by Ibidem on 2010-04-24
Glad to hear that it now works.
(I wonder what broke those, though?)

Regarding wireless, the hardware switch really does work both ways (at least with madwifi); sometimes, it seems that it got switched off accidentally, and I need to switch it on (like after hibernate/resume).
I know ath5k supports switch off, but am not sure about switch on.

---

