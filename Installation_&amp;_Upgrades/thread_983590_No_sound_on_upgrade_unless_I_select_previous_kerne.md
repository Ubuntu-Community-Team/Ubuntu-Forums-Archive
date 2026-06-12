---
title: "No sound on upgrade unless I select previous kernel"
date: 2008-11-15
forum: Installation &amp; Upgrades
---

### Post by tars_ac on 2008-11-15
I just upgraded from 8.04 to 8.10.  Everything went well, except for my sound.  The volume control has a "no" symbol through it, and shows the message:

> 
The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.

However, when I select kernel 2.6.24-21-386 instead of 2.6.25-2-386 in GRUB, my sound is back and everything works fine.  The sound panel shows no devices in 2.6.25.

Can anyone help?  I tried installing several gstreamer packages from Synaptic (even up to "ugly"), with no result.

Thanks,
loyal Linux fan

---

### Post by tars_ac on 2008-11-24
Does anyone have any ideas?

---

### Post by linux_tech on 2008-11-24
This may help-
```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list -O /etc/apt/sources.list.d/medibuntu.list && wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install -y ubuntu-restricted-extras non-free-codecs w32codecs totem-mozilla libdvdcss2
```

---

### Post by ExemplarUbuntu on 2008-12-03
I've just updated a Toshiba laptop from Heron to Ibex and have the same issue, I haven't tried an older kernel. Before I try the suggested fix, what does it do ?

Thanks.

---

### Post by tars_ac on 2008-12-06
linux_tech,

The packages installed fine, but there was still no sound even after a reboot.

ExemplarUbuntu,

I believe linux_tech's fix installs several restricted media software packages that include codecs and drivers that have patent or copyright restrictions in them.  Presumably, linux_tech was hoping that one of those might restore sound.  It didn't work for me, but it's possible it could help you.

Does anyone have any more ideas?  What is preventing pulseaudio from finding my sound card?

---

### Post by viaciofano on 2008-12-06
[http://ubuntuforums.org/showthread.php?t=843012&highlight=GStreamer+plugins+installed%2C+don%27t+sound+card+configured](http://ubuntuforums.org/showthread.php?t=843012&highlight=GStreamer+plugins+installed%2C+don%27t+sound+card+configured).

hi i found the link above which i think will help. i have the same issue as you and am slowly working through as i am a newbie to linux....
one quick option i looked at is 

try changing sound option
syste/prerences/sound
try change alsa to oss


then back again
regards Vinny

---

### Post by viaciofano on 2008-12-06
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

fixed it with the above link. for some reason my soundcard was not detected....
working perfectly now..:)

---

### Post by tars_ac on 2008-12-07
viaciofano, I followed the link you sent, and my sound is now working!

It is strange though.  The directions said to install the drivers using a terminal command, but it seems to have upgraded my system to 2.6.27-9-generic.  Maybe 2.6.25-2-386 was just a bad kernel version for my sound card.  I hope that being on the "generic" version of the kernel doesn't have any unforeseen consequences.

Thanks for your help!

---

### Post by viaciofano on 2008-12-07
thats ok i am like you learning and i guess thats part of it....

---

