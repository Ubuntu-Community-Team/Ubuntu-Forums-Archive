---
title: "Upgrade Graphics Card"
date: 2010-12-01
forum: Installation &amp; Upgrades
---

### Post by MacLeod_1980 on 2010-12-01
How do I go about upgrading my graphics card in ubuntu, I am moving from an NVIDIA, to and NVIDIA - can I simply switch it out?

---

### Post by sikander3786 on 2010-12-01
Not too difficult :-)

Which model is there and which one are you planning to install now?

I would recommend to remove the current Nvidia Proprietary drivers, replace your card with the new one and re-install Nvidia drivers. Simple!

---

### Post by MacLeod_1980 on 2010-12-01
I am moving from Asus EN8600GT Silent to Zotac GT430.

I am also wondering if I will get audio through this too, as some people have reported issues with XBMC.

So I should remove the restricted drivers and card, reboot machine, then power down and install new card?  Or just remove, power down and install new card?

---

### Post by sikander3786 on 2010-12-01
I would recommend removing the restricted drivers > Reboot > Power Down > Remove Card > Install New Card > Power On > Install restricted drivers.

Step by step :P

Don't know much about the sound issue though.

---

### Post by efflandt on 2010-12-01
I am using a Galaxy GT 430 and it works fine in Ubuntu.

Which Ubuntu?  If running maverick and you used System > Administration > Additional Drivers to "activate" them, simply use that to "remove" them.  Then shutdown, swap out the cards, reboot and with Additional Drivers "activate" nvidia.

Although, if nvidia-current in maverick is still 260.19.12, you might want to add x-swat to your repositories to grab 260.19.21 **before** you "activate" nvidia for the new card.

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates

sudo apt-get update
```Then "activate" nvidia, reboot and you will have nvidia 260.19.21. [http://www.ubuntuupdates.org/ppas/27](http://www.ubuntuupdates.org/ppas/27)

The current kernel 2.6.35-23-generic includes alsa modules that support its HDMI audio (3.6.35-22 does not unless you add alsa snapshot ppa).  But you need to figure out which of the 4 HDA NVidia devices work, by unmuting them in alsamixer and assuming card 1, also trying 1,7 1,8 and 1,9 in the following:

```
aplay -D plughw:1,3 /usr/share/sounds/alsa/Front_Center.wav
```For me 1,9 worked so I added the following to the section of /etc/pulse/default.pa that had alsa-sink commented out:

```
#load-module module-alsa-sink
**load-module module-alsa-sink device=hw:1,9**
```Then after reboot you should be able to select either your internal sound device for regular sound or **HDA NVidia** to get HDMI sound (ignore the other output device that says HDMI).  The speaker test in Sound Preferences will not work for HDMI sound, but if you open Rythmbox and play music or internet radio, you should be able to select either sound output on the fly.

Mine has a fan, but the fan is quiet and it idles only 3 C above room temperature (currently 20 C):

nvidia-smi -a

```
==============NVSMI LOG==============


Timestamp            : Wed Dec  1 18:34:59 2010

Driver Version            : 260.19.21


GPU 0:
    Product Name        : GeForce GT 430
    PCI Device/Vendor ID    : de110de
    PCI Location ID        : 0:1:0
    Board Serial        : 6203447409
    Display            : Connected
    Temperature        : 23 C
    Fan Speed        : 52%
    Utilization
        GPU            : 0%
        Memory        : 11%
```

---

### Post by MacLeod_1980 on 2010-12-03
This looks like excellent information, thanks for the input.

Thanks everyone, the upgrade worked - now just gotta see about the sound issues.

---

