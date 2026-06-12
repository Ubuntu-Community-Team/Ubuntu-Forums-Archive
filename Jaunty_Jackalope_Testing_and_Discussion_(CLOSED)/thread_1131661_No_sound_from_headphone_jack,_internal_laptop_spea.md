---
title: "No sound from headphone jack, internal laptop speakers work fine"
date: 2009-04-21
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by tomsa on 2009-04-21
[INDENT][/INDENT]I just installed the jaunty rc yesterday.  Everything is working really, really well so far except the fact that I'm getting no sound from my headphone jack.  After googling the crap out of my issues, I have found nothing, but I've posted my /etc/modprobe.d/alsa-base-conf below in the hope that it might grant someone who actually knows what they're doing some insight:

```
a# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2
```

The output of:```
cat /proc/asound/card0/codec#* | grep Codec
```is:

```
Codec: SigmaTel STAC9205
Codec: LSI ID 1040

```

I'm not really sure where to start with this, and I hope that I have given you something useful to work with.  I will gladly provide more information if you need it.  Thanks for your assistance!

TS

---

### Post by lithorus on 2009-04-21
Try and run alsamixer -Dhw

---

### Post by Zorael on 2009-04-21
Also, have a look at [http://ubuntuforums.org/showthread.php?p=5017453#post5017453](http://ubuntuforums.org/showthread.php?p=5017453#post5017453).

---

### Post by tomsa on 2009-04-21
Well, so far no progress.  I tried running alsamixer -Dhw just in case I had missed anything in all my prior volume changing/ muting/unmuting excursions just to be sure that I didn't miss a channel accidentally.  No dice there.  Same with gnome-alsamixer and the volume applet.  So, I tried editing my /etc/modprobe.d/alsa-base.conf by adding the line:
```
options snd-hda-intel model=gateway
```
as my laptop is a gateway t-1625, but that didn't work.  I looked at my prior post and saw that my sound card was listed as a stac9205 (not stac92xx) so I tried changing the line that I added to:
```
options snd-hda-intel model=dell-m42
```
also, to no avail.  I know there are two more possible options for the stac9205 sound card, but I have to go to work now, and I will try those later.  The following is the full /etc/modprobe.d/alsa-base.conf I'm using at the moment- in the case that someone might notice some other problem.  
```
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2
options snd-hda-intel model=dell-m42

```

I hope that I can get this working now, and don't have to wait for the official release to have it fixed.  Of course, that is assuming that it will be fixe for the initial release.  Meh.

---

### Post by Zorael on 2009-04-21
```
	STAC9205/9254
	  ref		Reference board
	  dell-m42	Dell (unknown)
	  dell-m43	Dell Precision
	  dell-m44	Dell Inspiron
```
Tried them all?

Lastly, you may want to try upgrading ALSA, either via a new kernel or by compiling new modules from source. A quick forum search turns up with a script that automates this; [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137).

---

### Post by tomsa on 2009-04-21
Not yet- I still have to try dell-m43 and dell-m44.  I had to leave for work before I got to try them (he said from his office computer)  I will try those two after I'm done and post the results.  

Just because I'm thinking about it at the moment, after looking at the output I got for:

 Code:
cat /proc/asound/card0/codec#* | grep Codec

which was:

Code:
Codec: SigmaTel STAC9205
Codec: LSI ID 1040

Is it possible (if neither the dell-m43 or dell-m44 lines work)  that the OS autoselected the wrong codec entirely?  That's just a thought.  Thanks again!


Thanks!

---

### Post by tomsa on 2009-04-21
> **Zorael said:**
> ```
	STAC9205/9254
	  ref		Reference board
	  dell-m42	Dell (unknown)
	  dell-m43	Dell Precision
	  dell-m44	Dell Inspiron
```
Tried them all?



I have tried them all now that I am home!  Unfortunately for me, none of them worked.  I was thinking about trying the ALSA upgrade you pointed me to but I have a quick question regarding that- should I restore my /etc/modprobe.d/alsa-base.conf to it's original state before I do so, or should I just press on?  I don't want to create any new breakages before I even get a chance to fix what's wrong now.

---

### Post by tomsa on 2009-04-22
I ran the ALSA upgrade script, and I still have no sound from the front headphone jack.  I now have enough changes made that I am starting to get confused and moderately forgetful as to what I've tried.  Ugh.  I did also try this to get more information along the way, and I wonder if it is at all telling:

```
tomsa@tomsa-laptop:~$ sudo modprobe snd-STAC92xx
 
FATAL: Module snd_STAC92xx not found
```

Now, I don't know just how much this does mean, since the internal speakers are still working.  I also have more than a few additional entries in the Applications>Sound & Video menu that don't seem to do anything at all:

Echomixer
Envy24control
HDSPMixer
HDSPConf
Rmedigicontrol

Nor do I know where they came from, or what to do with them.

Do you have any other ideas?  Should I just wait for the actual release and scrap this install?  Should I expect this to be fixed by the release at all?  I think that is highly unlikely as I haven't gotten any updates at all in the past 24-48 hours or so- and I have been checking for them.  This is starting to get frustrating!

---

### Post by Zorael on 2009-04-22
The module's name is still **snd-hda-intel** (or **snd_hda_intel** depending on in which context); STAC92xx is just the sound chipset model.

---

### Post by tomsa on 2009-04-22
I looks like I may be suffering from a known bug that affects anyone using the STAC9205 drivers for sound.  Bummer.  I really liked Jaunty.  I've attached the output of the alsa-info script that I also posted to launchpad at: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/306755](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/306755)

Thanks again for all the help!

TS

---

### Post by tomsa on 2009-04-22
I also tried the debian package alsa-driver-linuxant that was posted on the launchpad site.  Still nothing.  Meh.

---

