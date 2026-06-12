---
title: "[SOLVED] Another sound problem with Hardy Heron"
date: 2008-09-09
forum: Installation &amp; Upgrades
---

### Post by linuxonbute on 2008-09-09
This is the info about my laptop ( Zepto Znote 3215W )

uname -r
2.6.24-19-generic

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Headset [Logitech USB Headset], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

lspci
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

I have to mess around to change from the built in speakers to my usb headset. Each time it is hit and miss as to whether it will work.

Also with one setup I can get sound from Audacity but not Movie player etc.
With a different setup it is the other way round.
Any idea what i need to do?
Thanks

---

### Post by P13808 on 2008-09-09
[SIZE="6"][SIZE="4"]Make sure all the programs are in sync with each other on what device to use.  [/SIZE][/SIZE]



[SIZE="1"]also make sure the volume is high enough, i was about to add drivers after awhile on irc when i realized i never even turned on the volume(i even bought new speakers)[/SIZE]

---

### Post by linuxonbute on 2008-09-15
> **P13808 said:**
> [SIZE="6"][SIZE="4"]Make sure all the programs are in sync with each other on what device to use.  [/SIZE][/SIZE]

It seems that you are saying I tell the program what to use but there seems to be no option to do that hence my question in the first place
> 
[SIZE="1"]also make sure the volume is high enough, i was about to add drivers after awhile on irc when i realized i never even turned on the volume(i even bought new speakers)[/SIZE]

Well I do adjust sound levels as required.

If I choose to work with Audacity I have to set the device to one thing.
However if I use movie player I have to set it to some other thing.
Also it makes no difference if the program is already running. I have to close it, alter sound settings and then re-start it.
Any other ideas please?

---

### Post by linuxonbute on 2008-09-16
I have uninstalled pulseaudio, re-installed alsa and now they do all seem to work!

So is this a pulseaudio problem? A didn't have problems with Gutsy Gibbon.

Hope this helps someone else with these problems.

---

