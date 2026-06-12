---
title: "Mac Mini G4 PPC Lubuntu 13.04 Install Basics How To Tutorial"
date: 2013-05-05
forum: Installation &amp; Upgrades
---

### Post by Rahbee Kannuhn on 2013-05-05
Firstly, for the most part, this is information I gleaned from utilizing old tut's for other versions of Ubuntu and various wikis; the only thing I stumbled across myself was having yaboot go to 16bit to get things working; so with that said, thank you to everyone I learned from, you are my anonymous heroes.

Get the liveCD of Lubuntu to boot and have a working ui and working installer:
if standard boot, and boot work arounds does not work for you, try the following, modify to meet your monitors values, the important thing being set it to 16bit. This resolved my video issue from liveCD utilizing a Hanns-G monitor with my G4 Mac Mini and Radeon 9200 gpu.
```
[INDENT]** live video=radeonfb:1440x900-16@60**
[/INDENT]

```

[LIST]
[*]WIFI: 
[/LIST]
```
[INDENT=2]sudo nano /etc/modprobe.d/blacklist.conf
[/INDENT]

```[INDENT=2]
hash out the line "blacklist bcm43xx", make it look like the following:
```

# blacklist bcm43xx
```

install the following packages:
[/INDENT]

[LIST]
[*=2]b43-fwcutter 
[*=2]firmware-b43-installer 
[/LIST]
[INDENT=2]
I tried the legacy installer package and it did not work, if the installer I mention does not work you can try the legacy. I utilized the u.i. for this, in specific, Synaptic Package Manager; if you prefer command line, by all means sudo apt-get after it :v
[/INDENT]

[LIST]
[*]Sound: 
[/LIST]
[INDENT=2]```
sudo nano /etc/modules
```

add the following:

```
snd_aoa_i2sbus
snd_aoa_fabric_layout
snd_aoa_codec_tas
snd_aoa_codec_onyx
```

This will have your G4 Mac Mini doing its basics, you can now procede to make it your own.
[/INDENT]

Enjoy.:popcorn:

---

