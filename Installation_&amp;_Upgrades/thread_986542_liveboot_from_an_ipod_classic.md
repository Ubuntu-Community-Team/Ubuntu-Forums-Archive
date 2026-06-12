---
title: "liveboot from an ipod classic?"
date: 2008-11-18
forum: Installation &amp; Upgrades
---

### Post by fINTiP on 2008-11-18
I have here a 160 gig ipod classic, and with all the music I have that I put on, I still have over 100 gigs available- and I've been copying for the past 2 hours.

So I was wondering what I could do to take up all the space... I thought about just backing up my harddrive, but even if I just wholesale copied it I'd have more than half left- the harddrive itself is only 40 gigs, and I still have 12 gigs free on it.

So I was reading about how floola, for windows at least, can be installed on to the ipod itself and loaded off of the ipod to manage it from whatever computer you are on. I thought about doing that... but then I thought- why not just have a whole live boot on it?

Is this possible? Have other people done it? I'm not talking about ipodlinux- I don't want linux to run "on" the ipod, just from the ipod, as if it were any other usb jump drive.

I know I can put it in to disk mode, so it seems like it should be possible- but then again, ipods are a PITA... so I can imagine it easily not working. A quick google didn't show anything, so...

Anyone know anything about this? Otherwise, do you have any other ideas for blowing 50-100 gigs of space?

Also, is there a better forum to place this in, besides general help? I tried apple users, got no response... was thinking about hardware, but it seems to be primarily related to install and compatibility issues... still, that might work...

L

---

### Post by zwygart on 2008-11-18
I installed a lot on a USB flash drive (4 working OS at the same time + some others). I never heard from installing on a IPOD. But logically it should work. If you want Multi-boot I suggest install GRUB and patition your IPOD with a extended partition. 

If you only want a "liveCD" on your IPOD, I think this should work (it worked for me USB flash drive): 
Download the ISO. 
Extract the content on the root of the drive.
Install syslinux  (check syslinux.org).
Boot by choosing the right drive.

It is easier if you install on a separate partition (FAT), but it may be impossible.

I hope that partition an IPOD will not break it. Please post back about your experience.

P.S.:Where did you get infos about how to install to IPOD?

---

