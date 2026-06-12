---
title: "/proc/asound missing but ALSA installed"
date: 2016-05-09
forum: MINT
---

### Post by Mamoth on 2016-05-09
Hello to all.

I have been struggling with a sound problem for a while. There used to be sound available through my headphones but not the internal speakers.
Trying to fix it, I installed the latest version of the Realtek drivers ([http://www.touslesdrivers.com/index.php?v_page=23&v_code=41375](http://www.touslesdrivers.com/index.php?v_page=23&v_code=41375) ) and now I have no sound at all whatsoever.  :(

The computer is a DELL Latitude E5540 with Linux Mint 17.1  upgraded to  17.3 (the sound problem started before the upgrade to 17.3).

From what I understand, ALSA is installed but the sound card is not recognized at all any more. The folder */proc/asound* has simply disappeared. 

I have run this ALSA diagnostic script :  [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)
And the result is available here : [http://www.alsa-project.org/db/?f=86b3a09178d025f679e4606673ea3a35bf2e75e8](http://www.alsa-project.org/db/?f=86b3a09178d025f679e4606673ea3a35bf2e75e8)
One can see that the Driver version and the Library version of ALSA are left void.

I have tried re-installing the package *alsa-base*, to no avail. 

The sound card chip is Realtek ALC292. You may find a HardInfo report here : [http://www.filehosting.org/file/details/568133/hardinfo_report%202.html](http://www.filehosting.org/file/details/568133/hardinfo_report%202.html)


The content of the file */etc/modprobe.d/alsa-base.conf* is below :
```
~ $ cat  /etc/modprobe.d/alsa-base.conf 
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
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2


```

**Does any one have an idea of how to solve this ?**
I wish to avoid reinstalling the whole OS.

---

