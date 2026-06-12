---
title: "Acer Inspire 5570 Audio seriously broken"
date: 2007-11-10
forum: Installation &amp; Upgrades
---

### Post by gregsmith_to on 2007-11-10
[I]  **READ THIS FIRST** Fixed! I don't know why, but I have 6 linux choices on the grub menu, I guess they are three different kernels, each in normal and recovery mode. The kernels are all designated 7.10, and numbered 2.6.22-14, -16, -15 (in that order). I've been booting the first choice, -14. When I boot the -16, the sound driver works, and I was back to the normal 5570 problem (turn up 'surround' vol to hear speakers). I've set grub to boot -16 by default. Leaving the rest of the post as is.
[/I]

I have this Acer Aspire 5570 I got in September; I originally installed Feisty on it. The sound didn't work; I found instructions somewhere (very similar to those here : [https://wiki.ubuntu.com/LaptopTestingTeam/AcerAspire5720](https://wiki.ubuntu.com/LaptopTestingTeam/AcerAspire5720))
 on how to build and install more recent ALSA drivers, and that fixed it. When I upgraded to 7.10, the sound stopped working again; in retrospect it seems this may have been due to a mixer setting, but I assumed it was because my 7.04 fix had been over-written by the upgrade. So, I followed the instructions on this page
[http://ubuntuforums.org/showthread.php?t=305712](http://ubuntuforums.org/showthread.php?t=305712)
 using the most recent alsa code. I got part way through this, but the build in step 7 failed. I've no idea why; the error message does not hit on google which is always a very bad sign.

So, I have a machine with no functioning sound driver at all. I'm trying to reinstall the 7.10 default state, and that isn't working either. I've gone through the Synaptic Package manager and reinstalled about everything that looks like it's related to sound, and rebooted; no change. In particular it shows alsa-base at 1.0.14-1ubuntu2 and alsa-utils at 1.0.14-1ubuntu4.
 

Various info:
[LIST]
[*] system log shows this at boot (7 lines shown out of about 50 similar):
```

Nov 10 13:57:52 siena-laptop kernel: [   14.712000] snd_hda_intel: disagrees about version of symbol snd_ctl_add
Nov 10 13:57:52 siena-laptop kernel: [   14.712000] snd_hda_intel: Unknown symbol snd_ctl_add
Nov 10 13:57:52 siena-laptop kernel: [   14.712000] snd_hda_intel: disagrees about version of symbol snd_pcm_new
Nov 10 13:57:52 siena-laptop kernel: [   14.712000] snd_hda_intel: Unknown symbol snd_pcm_new
Nov 10 13:57:52 siena-laptop kernel: [   14.712000] snd_hda_intel: disagrees about version of symbol snd_pcm_limit_hw_rates
Nov 10 13:57:52 siena-laptop kernel: [   14.712000] snd_hda_intel: Unknown symbol snd_pcm_limit_hw_rates
Nov 10 13:57:52 siena-laptop kernel: [   14.712000] snd_hda_intel: disagrees about version of symbol snd_card_register

```
  
 
[*] Device manager says there is an "82801G (ICH7 Family) High Definition Audio
Controller". Status is "Status", Bus Type "PCI". I'd also include all the other 
information it gives on the Advanced tab, but there
appears to be no way to export or paste info from the Device Manager.
 
 
[*]alsamixer says:
```

    alsamixer: function snd_ctl_open failed for default: No such device

```
[*]The little volume control icon says this when I click on it
```

   "no volume control GStreamer plugins and/or devices found"

```
[*] alsaconf: sounds like it might be useful, can't find it anywhere on my machine. Except in the alsa-utils source dir, where it seems to be improperly built.  And I already have an ubuntu 'alsa-utils' installed, so I should have it somewhere, no?
 
[*]Below is the error message from 'make' in alsa-utils. The fact that the file is missing indicates that the previous command invoked by make (before a &&) succeeded, but failed to create the file. The makefile is complex and I haven't figured out enough of it to be useful here.

[/LIST]

```
 
 Making all in po
make[2]: Entering directory `/home/greg/alsa2/alsa-utils/alsaconf/po'
mv: cannot stat `t-ja.gmo': No such file or directory
```

I just went through the process described in [https://wiki.ubuntu.com/LaptopTestingTeam/AcerAspire5720](https://wiki.ubuntu.com/LaptopTestingTeam/AcerAspire5720)
and the build/install went as expected, but there is no change - , I still have no device as far as the system can tell.

Other than doing a full reinstall, what can I do to unbreak the sound?

One more thing: content of /etc/modprobe.d/alsa-base:
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
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
options snd-hda-intel model=acer


```

---

### Post by rajaiskandarshah on 2007-12-02
i have ubuntu 7.10 on acer aspire 5570. fresh install from cd.

initially, there was no sound. fixed it as follows:

1. double click on the volume control icon on the top right panel
2. alsa mixer window will open
3. unmute the pc speaker and increase volume
4. go to menu edit > preferences
5. volume control preferences window will open
6. select surround
7. close volume control preferences window
8. unmute the surround and increase volume

on my sound preferences i have 
1. HDA Intel (alsamixer)
2. Realtek ALC883 (OSS mixer)

hopefully this will help if you intend to do a fresh install

:popcorn:

---

