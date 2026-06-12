---
title: "Jaunty - Crackling sound in Flightgear, Supertux, Supertuxkart"
date: 2009-04-14
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by george1984 on 2009-04-14
Sound is perfect except for these three apps. (Sound in Hardy is perfect in all aspects).

This is not  sound  distortion as such – more like the effect you would experience from a loose wire.

Equipment :	Mainboard		Asus A8N5X
		Graphics		GeForce 7300 LE
		Sound Card		Soundblaster CA0106

OS					Jaunty_32 ext3



sudo cat /proc/asound/modules 

0 snd_ca0106 
 1 snd_intel8x0 

sudo gedit /etc/modprobe.d/alsa-base

 autoloader aliases 
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


	For test purposes, install Jaunty on second box :-

Equipment :		Asus P2
			No Graphics Card
			Soundblaster CA0106

			OS Jaunty_32 Beta ext3 (no updates!)

	On this box supertuxkart and supertux sound is perfect (flightgear not tested).


		Has anyone else had a similar experience?

---

### Post by hyperdude111 on 2009-04-14
I have had crackling audio problems in jaunty but not with any particular app it just randomly happens. I found to set it to normal again I play around with the "PCM" setting in volume preferences.

---

### Post by george1984 on 2009-04-14
Tried all of the combinations I could think of. Still crackling. 

Is there something that these three apps. have in common?

---

### Post by lunarcloud on 2009-04-14
Non Creative Sound cards are affected by an OpenAL bug, which most of these games use.

[https://bugs.launchpad.net/ubuntu/+source/openal/+bug/194919](https://bugs.launchpad.net/ubuntu/+source/openal/+bug/194919)

---

