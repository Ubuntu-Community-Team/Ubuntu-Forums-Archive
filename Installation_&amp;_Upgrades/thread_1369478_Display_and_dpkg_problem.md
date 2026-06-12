---
title: "Display and dpkg problem"
date: 2010-01-01
forum: Installation &amp; Upgrades
---

### Post by JPKowal on 2010-01-01
I'm relatively new to Linux. I have an ACER Aspire laptop with a SIS M760GX Video card.

Seems like everyone has a problem with this card. It appears that I can fix it if I run:

sudo dpkg-reconfigure xserver-xorg or
sudo dpkg-reconfigure -phigh xserver-xorg

This does not seem to want to work. It does not open a GUI where I can edit my cards settings, which is what one post said it would do

It does nothing, just takes me back to the prompt with no message at all.

is there something wrong with my xserver-xorg package or what?

Thank you in advance,

 BTW, this seems pretty silly that it's this difficult to get to your video settings. I think that's pretty important. Very important if you can't see or if I am going blind by this constant flickering to where I really want to just turn off the computer. But, since XP has crashed again I figured I will try this again.

---

### Post by tommcd on 2010-01-01
What version of Ubuntu is this?
You can try booting to recovery mode and choose the option "xfix fix video" (or whatever it says exactly). Then when that finishes reboot and see if the video is better.
This is a confirm bug in Ubuntu. The bug is likely upstream, meaning that it is part of the linux kernel. I don't think it has been fixed:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-sis/+bug/287475](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-sis/+bug/287475)

And welcome to the Ubuntu forums!

---

