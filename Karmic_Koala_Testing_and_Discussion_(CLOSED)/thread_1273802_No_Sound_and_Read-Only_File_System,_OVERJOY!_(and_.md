---
title: "No Sound and Read-Only File System, OVERJOY! (and some other stuff...)"
date: 2009-09-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by flamefury on 2009-09-23
Well, as a last-ditch effort to get sound to work on Ubuntu distributions, I tried my hand at the Alpha 6 of this. But (expected it really) sound still refuses to function at all.

aplay -l output:
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC663 Analog [ALC663 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC663 Digital [ALC663 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```lspci output:
```

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation G94 [GeForce 9800M GS] (rev a1)
03:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
07:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
07:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
```


In addition to this, I am unable to alter anything on my data partition. I have set my hard drive into three partitions, one for Vista, one for Ubuntu and one for general purpose information that I want to be able to use on either OS. It defeats that purpose if I can't access it on one.

fdisk -l output:
```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x97646c29

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1530    12289693+  82  Linux swap / Solaris
/dev/sda2   *        1531        8032    52226992    7  HPFS/NTFS
/dev/sda3            8033       14559    52428127+  83  Linux
/dev/sda4           14560       38913   195623505    5  Extended
/dev/sda5           14560       38913   195623473+   b  W95 FAT32

```


And finally, my computer won't stop default setting on Canada keyboard. I have to go into it and change it back to Canada -English every time. Anyway to fix this?

---

### Post by flamefury on 2009-09-23
Well, isn't this interesting. I tried purging the alsa stuff (linux-sound-base, alsa-utils, alsa-base and alsa-oss) and then reinstalling, as well as install gnome-alsamixer. Now aplay can't read any sound card, and neither does the gnome alsamixer.

EDIT: Nevermind. I also tried using the typical fix for my chipset by adding three lines to the alsa-base.conf file. 
#options snd-hda-intel model=3stack-dig
#options snd-hda-intel enable_msi=1
#options snd-hda-intel single_cmd=1

Commenting that stuff out and rebooting got my card visible again.

EDIT2: Well, my computer's onboard microphone works, as does the speakers. I set my input WAAAAY high along with the output in alsamixer to try and get sound to work in general. Unfortunately, it still can't PLAY anything from the computer itself. So far, all I can do is receive an echo by talking into the mic and listening to the speakers. Very, very peculiar.
In addition, I added these lines to etc/modprobe.d/alsa-base.conf
```
options snd-pcsp index=-2
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
```
Unsure if they're the reason behind the microphone and speakers working as they do, as it could have just been changing the settings in alsamixer.

---

### Post by Reiger on 2009-09-23
ALSA stuff shouldn't be touched (unless, perhaps you are installing OSS) because that provides things like hardware drivers for your sound card/chip.

It may be some kind of weird pulse-audio/alsa (how they interact I mean) misconfiguration; personally had a bit of trouble with pulse-audio on Jaunty which I got around by removing pulse-audio entirely. (Using Kubuntu & phonon has ALSA backends so nothing lost there.) There are people more knowledgeable on this matter than me out there, though.

EDIT: About the read-only file system; it may be an unclean shutdown from Vista which marked the (presumably) NTFS partition as &#8216;locked&#8217;. (Had that happen a few times.) You may want to try a cold boot & clean shutdown cycle with Vista; then boot Karmic to see if it is fixed.

---

### Post by flamefury on 2009-09-23
Gonna try the pulseaudio suggestion.

I'm currently logged into Vista. I found, by far, the most peculiar set of files in my data drive...
[http://img27.imageshack.us/img27/6154/screenofweirdness.jpg](http://img27.imageshack.us/img27/6154/screenofweirdness.jpg)

I don't know what happened here, because the information given is clearly wrong (some were modified at 2069? File size is shown as grossly huge too, which is inaccurate). Whether or not this has to do with Karmic, I don't know. I'll see what I can do, since this is an Ubuntu forum and not Vista. Hoping it'll just disappear.

Going to shutdown, tell you the results.

EDIT: Nope, still can't do squat to the data drive. That C++ folder also has the weirdness going on in Linux, although not nearly as extensive as it was in Vista:
[http://img44.imageshack.us/img44/4466/screenshothv.png](http://img44.imageshack.us/img44/4466/screenshothv.png)
The thing is, I tried deleting this folder before in Jaunty, before I reformatted my Linux drive and put in Karmic. Is this a left over remnant?

Oh right, and the data drive is FAT32, if that's relevant.

---

### Post by Reiger on 2009-09-24
I don't know: I never, ever saw that; it almost seems like it is just the physical data of your disk without any real file-mapping (i.e. some contiguous blocks of hard disk are represented as file, other as meta data... but what gets to be what is sort of random).

If you are sure you don't care about any of that data; I'd advise to reformat it (as whatever file system it was supposed to be in the first place). Backup what you can't afford to loose first etc. ..

---

### Post by flamefury on 2009-09-24
Reformat complete, I can now read and write files on both Vista and Linux. That crazy pile of files also disappeared on both ends.

Now, for the sound issue. Hrm. Removing pulseaudio didn't work. I installed it back on any way.

---

### Post by flamefury on 2009-09-28
Can I try downgrading my alsa version? How would I go about doing this?

---

### Post by flamefury on 2009-09-29
I got it to work!! OMGOMGOMGOMGOMGOMG...
I don't know what I did, it could have been to add "options snd-hda-intel enable-msi=1" to both /etc/modules.conf and etc/modprobe.d/alsa-base.conf. That was the most recent change I can remember trying. I also don't have PulseAudio on my system anymore.

However, headphones fail to work. In addition, totem player doesn't do squat. So far, I'm limited to listening directly off YouTube videos.
Do I need some kind of driver for headphones too?

EDIT: RhythmBox works. Just Totem seems to fail. Headphones are being pain.

---

