---
title: "[BUG]Headphone - No Sound"
date: 2009-04-03
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by thyams on 2009-04-03
Problem: Headphones do not receive audio.  Speakers work fine.

BIZZARO: Noticed is if I plug it in 3/4 of the way in in the port, I hear everything fine.  The headphones are good though, tested them in an mp3 player, a TV, and another laptop.

_**Laptop Hardware**_**:**
**Operating System**:                Ubuntu Jaunty 64-bit 9.04-Beta
**Model**:                                  ASUS G50Vm-X1
**Processor**:                            Intel Core 2 Duo @ 2.00GHz/2.00GHz 4MB Cache FSB 800 MHz
**System Ram**:                        4096 MB DDR2 Dual Channel 667 MHz
**Display**:                                nVidia 9700M GT 512 MB GDDR3 (Driver 180.44 Installed @ 1366x768x24)
**Sound**:                                 Realtek HD Audio Codec ACL663 w/ 3-Port SPDIF/Headphone Audio Port
                                            nVidia HDMI Video/Audio Out
**HDD**:                                    200 GB 7200 RPM SATA-II (Running in Enhanced)

Previously Tried Operating Systems:
!# CrunchBang 8.10 64-bit - Speakers and Headphones did not work.
Ubuntu 8.10 64-bit - Speakers did but Headphones did not work.
Windows XP Pro 64-bit - Speakers and Headphone jack works.
Windows Vista 64 - Home Premium - Speakers and Headphone jack works.
ASUS Boot Screen - Speakers and Headphone jack works.

ALSA Technical Info For My Laptop:
[http://www.alsa-project.org/db/?f=05f1d2ef3fb8ebe97c0a7a9c6a475c5dc52b65ac](http://www.alsa-project.org/db/?f=05f1d2ef3fb8ebe97c0a7a9c6a475c5dc52b65ac)

Notes:
Know there are many posts on it, I have read the majority, still no solution for me. Alsamixer says its the nVidia HDMI when open, still cannot change the volume of Headphones (0,0).  Volume Control: No headphone option, just master, and speaker. Switch tab has Headphones checked. Went ahead and installed ALSA 1.0.19 to see if that fixed. Alas I am here.


**_Configured ALSA (1.0.19):_**
This was necessary as to begin with I had no volume in speakers or headphones on a fresh install.

> sudo nano /etc/modprobe.d/alsa-base.conf

Added these two lines:

> options snd-hda-intel model=g50v
> options snd-mcp78 index=-2


aplay -l
> **** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC663 Analog [ALC663 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC663 Digital [ALC663 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

cat /proc/asound/card0/codec#* | grep Codec
> Codec: Realtek ALC663
Codec: LSI ID 1040
Codec: Nvidia MCP78 HDMI

amixer
> Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pswitch
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [on]
  Front Right: Playback [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958',1
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 0 [0%] [-16.50dB] [off]
  Front Right: Capture 0 [0%] [-16.50dB] [off]
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Mic' 'Front Mic' 'Line'
  Item0: 'Mic'
Simple mixer control 'Speaker',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'i-Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]

**_Things Tried:_**
1.) Rebooted the Laptop again with headphones already in. This let me hear the GDM login sound very very very faint and no sound can be heard past GDM.

2.) Checked ALSA mixer to make sure it wasn't muted.  Headphones are unmuted but unable to regulate any volume control with it.

3.) Unplugging the headphones immediately gives me volume to speakers.

4.) BIOS has post test sound ON, volume level set to low.  No issues though with it on.  If disabled however, I have no sound in speaker or headphones.

5.) Tried in terminal: > sudo alsa force-reload  This did not work, however if you lose sound intermittently this can often fix it.


Informative Links:
1.) Checked this link for installing ALSA 1.0.19 from source.
[https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/65078](https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/65078)

2.) Various ALSA troubleshooting ideas.
[http://ubuntuforums.org/showthread.php?t=806620](http://ubuntuforums.org/showthread.php?t=806620)

3.) This link has the ALSA upgrade script.
[http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)

---

### Post by thyams on 2009-04-06
Bump

---

### Post by taavikko on 2009-04-06
Check again using "alsamixer -Dhw"
turn channels up one at a time, to see if it helps.

Also, it may be other "model=*" to use.

Notice, don't have to reboot to test them
just "sudo rmmod snd_intel" and then modprobing it again "sudo modprobe snd-intel options here"

---

### Post by thyams on 2009-04-06
Appreciate the post, but nothing changed. Tried all the ASUS options for model, nothing worked, tried also

probe_mod 1 option.

I only get sound when the cable is only plugged in halfway and balanced.

It seems to me that the ALSA drivers have S/PDIF and Headphones backwards.  I have all but given up on this damn problem.  The only Linux issue I have.

---

