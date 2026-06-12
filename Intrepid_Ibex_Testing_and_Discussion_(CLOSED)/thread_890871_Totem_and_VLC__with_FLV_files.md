---
title: "Totem and VLC  with FLV files"
date: 2008-08-15
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by landcross on 2008-08-15
I have an issue with Totem and VLC which both just close when I try to open a FLV file.

VLC is OK when playing MP3. BUt for some reason Totem stops after about  seconds.

No problems with sound in other areas. 

Flash videos play OK in Firefox but not downloaded FLV files

---

### Post by Nullack on 2008-08-15
Get the good,bag,ugly and ffmpeg plugins for gstreamer and totem will be fine with flv as well as others

---

### Post by Nullack on 2008-08-16
To better help here's one of the test files I use for FLV testing:

[http://samples.mplayerhq.hu/FLV/asian-commercials-are-weird.flv](http://samples.mplayerhq.hu/FLV/asian-commercials-are-weird.flv)

Everybody DANCE :lolflag:

---

### Post by landcross on 2008-08-16
I had the plugins already installed but other suggestions  to get it working appreciated!

I don't want to go back to windows!

---

### Post by Martje_001 on 2008-08-16
Install the package '**ubuntu-restricted-extras**' from Synaptic and see if everything works now.

---

### Post by Nullack on 2008-08-16
> **landcross said:**
> I had the plugins already installed but other suggestions  to get it working appreciated!

I don't want to go back to windows!

Quite simply you dont have the required plugins installed properly then. Make sure you have the good, bad, ugly and ffmpeg gstreamer plugins installed and that you are actually using Totem with the gstreamer backend.

---

### Post by landcross on 2008-08-18
Have reinstalled everything twice, but Totem and VLC both close when I try to open a FLV file. I have no problem with MP3 files.  [on a clean install of Intrepid]

This may be my problem, if so how do I fix?
sudo totem --debug

** (totem:8844): WARNING **: Failed to create dbus proxy for org.gnome.SettingsDaemon: Could not get owner of name 'org.gnome.SettingsDaemon': no such name



Plugins
gstreamer0.10-tools is already the newest version.
gstreamer0.10-x is already the newest version.
gstreamer0.10-plugins-base is already the newest version.
gstreamer0.10-plugins-good is already the newest version.
gstreamer0.10-plugins-ugly is already the newest version.
gstreamer0.10-plugins-bad is already the newest version.
gstreamer0.10-ffmpeg is already the newest version.
gstreamer0.10-alsa is already the newest version.
gstreamer0.10-schroedinger is already the newest version.
gstreamer0.10-pulseaudio is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by Nullack on 2008-08-18
Please host a sample online so I can look at it in detail

---

### Post by landcross on 2008-08-19
Not sure what you mean
'host a sample online'

If you mean the files, these are just FLV files that worked before moving to Intrepid.
I have sound in other programs so it may be a problem with the Video element in the file, although music Flash videos work fine when viewed on web with Firefox

---

### Post by Nullack on 2008-08-19
Use an online host like [http://www.filewind.com/](http://www.filewind.com/) or something. To diagnose it further I need samples of the files.

---

### Post by landcross on 2008-08-20
Installed Gxine to replace Movie player and can now play them

---

### Post by Nullack on 2008-08-20
Xine is more broken with regressions than gstreamer

---

