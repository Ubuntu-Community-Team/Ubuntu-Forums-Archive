---
title: "Upgrade to 10.04 Lost nVvidia, have No Graphics"
date: 2011-03-26
forum: Installation &amp; Upgrades
---

### Post by SedaliaSteve on 2011-03-26
I have a Shuttle SP35 that had been running Jaunty. I mainly left it alone since it was a music server. I had used the alternate Desktop to install it since it has a RAID 1. I had also removed pulseaudio since it didn't support the Intel audio and used OSS.

I chose upgrade to 10.04 from the Upgrade Manager and things went well at first. After a couple of days it prompted me for an update and I installed it. It required a reboot and went to hell. The driver for my nVidia G84 (GeFforce 8400 GS), an older card, was gone. Trying to bring up the system in low res just hangs. I can end up in terminal mode and run startx to get a terminal.

Can someone point me to command line ways to get back to a working graphics system? I wish I had never upraded. Jaunty might have been old but it worked.

Steve

---

### Post by SedaliaSteve on 2011-03-26
I did get video back. I purged the ubuntu-restricted-extras and re3installed it then installed gdm again. I now have video but no sound. All the pulseaudio is back. I have the Intel ICH9 HD Audio Controller and will have to see how to make that work.

Steve

---

### Post by Shplad on 2011-12-10
SedaliaSteve:

Don't mean to thread hijack, but it seems you solved your own problem...so...


It looks like the SP35 has the same Intel HD sound chip as my machine- the SP35P2 Pro - with an ALC88 codec as well.

Would you be kind enough to share your configuration? 

I have been working for days and have been unable to get (ALSA) sound working on my SP35P2 Pro. I think I've
messed things up more than fixed them.


Thanks


Shplad

---

