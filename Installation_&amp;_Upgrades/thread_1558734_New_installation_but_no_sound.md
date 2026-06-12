---
title: "New installation but no sound"
date: 2010-08-22
forum: Installation &amp; Upgrades
---

### Post by gievenden on 2010-08-22
New Ubuntu installation with a big problem: no sound.
 
OS: Ubuntu 10.4.1
Hardware: HP Pavilion Elite e9150t (64 bit)
Sound card: Creative Sound Blaster X-Fi Xtreme Audio

Preliminary checks of sound level settings and obvious dumb stuff but there is still no sound.

The problem seems to be that the system does not recognize the existence of the sound card and insists on using alternative audio devices.

1. Output of lspci
  ...
04:00.0 PCI bridge: Creative Labs [SB X-Fi Xtreme Audio] CA0110-IBG PCI to PCIe Bridge
05:00.0 Audio device: Creative Labs [SB X-Fi Xtreme Audio] CA0110-IBG
08:00.0 VGA compatible controller: nVidia Corporation GT216 [GeForce GT 220] (rev a2)
08:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)

2. Listing of 'cat /proc/asound/cards'

 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfbefc000 irq 16
 1 [Generic        ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xf9ffc000 irq 17

The above is also what shows up in the F6 selection in 'alsamixer'.

I found enough to probably isolate my problem but have absolutely no idea how to fix it.

Help would be greatly appreciated.

Thank-you.

---

### Post by mörgæs on 2010-08-23
This might help you:
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by gievenden on 2010-08-23
As it turns out, so far, there is no specific driver for CA0110 and snd-hda-intel is used instead. The last reference to this problem seems to be near the end of 2009 and I suspect that it is a dead issue and CA0110 will forever be an orphan.

For some odd reason, the video card is detected as an audio board and becomes one of the two audio types listed by alsamixer. Unfortunately, NVIDIA always comes op as index 0 and CA0110 as index 1. Because both are assigned the driver snd-hda-intel the method of flipping the order suggested by the previous reply reference does not work because of using the driver name as the key to changing order.

Arrgh! :mad:

Maybe another few hours on this before turning this beast into an anchor.

---

### Post by mörgæs on 2010-08-23
Have you searched Launchpad for this bug?

---

### Post by gievenden on 2010-08-23
As I said, according to [http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs)
there is not supposed to be a driver for CA0110. **_BUT_**, closer examination of /lib/modules/2.6.32-24-generic/kernel/sound/pci/hda/ I find the file:

snd-hda-codec-ca0110.ko

What bothers me is I don't know the significance of the "codec", but more importantly, why doesn't this get matched up with the hardware???

I wish I knew what I was doing. :mad:

---

### Post by whorider on 2011-01-11
I know, I know...Old Thread..But if someone stumbles across this like I did looking for a solution, here is what worked for me:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```

Then reboot:
```
sudo reboot
```

[https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules)

Maverick x64

---

### Post by Kuoi on 2011-02-27
> **whorider said:**
> I know, I know...Old Thread..But if someone stumbles across this like I did looking for a solution, here is what worked for me:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```

Then reboot:
```
sudo reboot
```

[https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules)

Maverick x64


WHORIDER !!! You're the man !!!!

Spread the word !!! Creative X-fi xtreme audio pci-e IS WORKING on Ubuntu Maverick 64 bit with your method !!

THANK YOU VERY MUCH !!!!

---

### Post by A. J. Rimmer on 2011-03-27
Also working now for me with Lucid Lynx LTS 64-bit.  This is great, so happy!

(I'm running the exact same system as gievenden.)

Quoting Kuoi:

"WHORIDER !!! You're the man !!!!

"Spread the word !!! Creative X-fi xtreme audio pci-e IS WORKING on Ubuntu Maverick 64 bit with your method !!

"THANK YOU VERY MUCH !!!!"

---

### Post by tigerstyle1 on 2011-04-02
All I can say is "whord"-up!  

Whorider, you really helped me out with this one.  Kudos * 10.

I've spent countless hours looking for a quick, elegant solution and finally found it here.

---

### Post by Vinencre on 2011-06-05
> **whorider said:**
> I know, I know...Old Thread..But if someone stumbles across this like I did looking for a solution, here is what worked for me:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```Then reboot:
```
sudo reboot
```[https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules)

Maverick x64
Thanks a lot !!! I was looking for it for days !!!

Yes, you're really the man ! :D

I confirm, Creative X-Fi Xtreme Audio PCI-E WORKS on Ubuntu, Lucid to Maverick, 32 or 64 bits version !!!
Same on Linux Mint and XBMC Live !

THANK YOU VERY MUCH WHORIDER !!!!!

---

### Post by Big Boyee on 2011-08-17
> **whorider said:**
> I know, I know...Old Thread..But if someone stumbles across this like I did looking for a solution, here is what worked for me:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```

Then reboot:
```
sudo reboot
```

[https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules)

Maverick x64

It appears I'm a bit late to this party, but wow. Thank you so much. I have spent HOURS trying to make this work, and this fixed everything. Thank you. If only I had found this thread first! It's a shame it's so buried.

---

### Post by D4rkshadow7 on 2012-02-05
Hello, I also have the sound blaster xtreme audio and I'm having troubles to make it work on ubuntu 11.10. I've been around 2 days trying to make it work but nothing. Now I see here some people which have been able to make it work, but with that steps doesnt work to me :(.

Since I installed ubuntu I can here some noise when I put the music or a youtube video, but its not what  it should be,

I tried that and when I write:
sudo apt-get install linux-alsa-driver-modules-$(uname -r)I get this error:
XXXXXX~$ sudo apt-get install linux-alsa-driver-modules-$(uname -r)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-alsa-driver-modules-3.0.0-12-generic
E: Couldn't find any package by regex 'linux-alsa-driver-modules-3.0.0-12-generic'
 I've tried in kernel 3.0.0-12 and 3.0.0-15 and I've the same message on both.

I'll really appreciate If somebody could help me. Thank you!

---

### Post by D4rkshadow7 on 2012-02-06
No one know anything?

---

### Post by mörgæs on 2012-02-07
This thread might help:

[http://ubuntuforums.org/showthread.php?t=1885240](http://ubuntuforums.org/showthread.php?t=1885240)

---

