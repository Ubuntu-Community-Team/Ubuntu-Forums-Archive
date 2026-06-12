---
title: "No sound after install, Audigy2 PCI"
date: 2005-09-03
forum: Installation &amp; Upgrades
---

### Post by Chillout on 2005-09-03
Hello.
I installed Hoary 5.04 and noticed I had no sound. I followed several guides to install XMMS and the MP3 plugin so I could test better.
During boot up, I can hear the speakers making a loud "thump" when the ALSA modules are being loaded.
I tried to fiddle with ALSAMIXER but to no avail.
Also tried to go to GNOME's Multimedia System Selector and change ESD to ALSA or OSS, but also to no avail.
Lastly I tried the "How to configure sound to work properly in GNOME?" guide in [http://ubuntuguide.org/#configuresoundproperly](http://ubuntuguide.org/#configuresoundproperly), but still no sound!

I have a Audigy 2 PCI sound card.

Can anyone help, please?
Thank you for reading.

EDIT: Ahhh, those marvelous little unknow and weird options in ALSAMIXER... unmute (with m key) the option "analog/digital output jack"

---

### Post by fuse3k on 2005-09-03
[QUOTE=Chillout]Hello.
I installed Hoary 5.04 and noticed I had no sound. I followed several guides to install XMMS and the MP3 plugin so I could test better.
During boot up, I can hear the speakers making a loud "thump" when the ALSA modules are being loaded.
I tried to fiddle with ALSAMIXER but to no avail.
Also tried to go to GNOME's Multimedia System Selector and change ESD to ALSA or OSS, but also to no avail.
Lastly I tried the "How to configure sound to work properly in GNOME?" guide in [http://ubuntuguide.org/#configuresoundproperly](http://ubuntuguide.org/#configuresoundproperly), but still no sound!

I have a Audigy 2 PCI sound card.

Can anyone help, please?
Thank you for reading.

EDIT: Ahhh, those marvelous little unknow and weird options in ALSAMIXER... unmute (with m key) the option "analog/digital output jack"[/QUOTE]
 Yea my Audigy 2 PCI is having problems too.

---

### Post by tktreload on 2005-09-03
Is that also after a fresh install?
I just installed a couple of hours ago

---

### Post by tktreload on 2005-09-03
I dont have an audigity card, but also have problems with the sound, after installing today.

do any of you have alsaconf?
I cant find the executable in my distro, allthough it's supposed to be there.  maybe thats a problem :???: 

my module is intel8x0
on 2.6.10-5-686-smp

---

