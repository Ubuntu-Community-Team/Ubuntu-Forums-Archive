---
title: "AsRock Core audio over HDMI issue"
date: 2011-01-28
forum: Installation &amp; Upgrades
---

### Post by daniel.jays on 2011-01-28
Hello all!

I've a problem with my AsRock Core and my audio over HDMI. Trying to get it work now for over 2 months.

On Ubuntu 10.04 it was working with the offical Realtek HDA Intel driver for Linux but on Ubuntu 10.10 the driver installation failed.

**uname -a**
```
Linux myMachine 2.6.35-25-generic #44-Ubuntu SMP Fri Jan 21 17:40:44 UTC 2011 x86_64 GNU/Linux
```**aplay -l**
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: VT2020 Analog [VT2020 Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: Intel [HDA Intel], device 1: VT2020 Digital [VT2020 Digital]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1

```**cat /proc/asound/version**
```
Advanced Linux Sound Architecture Driver Version 1.0.23.
```**head -n 1 /proc/asound/card*/codec#***
```
Codec: VIA VT2020
```**Hardware Specs**
[http://www.asrock.com/nettop/overview.asp?Model=Core%20100HT](http://www.asrock.com/nettop/overview.asp?Model=Core%20100HT)

**Alsa-Script**
[http://www.alsa-project.org/db/?f=fbaa7b33c700b240b660c9f6f5a515496a808599](http://www.alsa-project.org/db/?f=fbaa7b33c700b240b660c9f6f5a515496a808599)

Would be great if someone could help me :(

---

### Post by daniel.jays on 2011-01-28
anyone?

---

### Post by daniel.jays on 2011-01-30
bump

---

### Post by P4man on 2011-01-30
By asrock core, do you mean Core 100HT?
This guy here seems to suggest it works out of the box with 10.10:
[http://myplace.dk/2010/12/27/linux-on-asrock-core-100ht/](http://myplace.dk/2010/12/27/linux-on-asrock-core-100ht/)

Although he is using 32 bit. 

Can you provide the output of

```
lspci
```

---

### Post by daniel.jays on 2011-02-01
Yes, it's the Core 100HT.[B]

lspci[/B]
```

00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 12)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 12)
00:04.0 Signal processing controller: Intel Corporation Core Processor Thermal Management Controller (rev 12)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA IDE Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.5 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 2 port SATA IDE Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
02:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03)

```Can it be a problem of the 32 / 64 bit?

Currenty I've installed the latest ALSA-Snapshot. Analog sound output is working but no sound over HDMI.

**How can I remove all _alsa packages_ (including custom configs from Realtek drivers) / _pulse-audio packages_ and reinstall them as it was after the ubuntu-installation?**

I've tried:
```
sudo apt-get purge linux-sound-base alsa-base alsa-utils
```and
```
sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop
```as suggested in this thread:
[http://georgia.ubuntuforums.org/showthread.php?t=1643041](http://georgia.ubuntuforums.org/showthread.php?t=1643041)

but no luck.

---

### Post by daniel.jays on 2011-02-01
I've completely reinstalled the kernel, ubuntu-desktop, alsa and pulseaudio without the snapshots. Now the soundcard is recognized as it were with the ALSA-Snapshot.

I've no "HDMI Stereo" Option. I can only set:
"**Digital Stereo Output (IEC958 )**"
or
"**Digital Stereo (IEC958 ) Output + Analog Stereo Input**"

None of the them is working. All the other options are for Analog.

---

### Post by P4man on 2011-02-01
Id try booting a 32 bit livecd, see if it works in a live session.

---

### Post by daniel.jays on 2011-02-01
This is what I've done now.. with a 64bit Ubuntu Live CD..

Using the Live CD I have 2 more sound profile options:
"**Digital Stereo (HDMI) Output**"
and
"**Digital Stereo (HDMI) Output + Analog Stereo Input**"

With this profile selected the sound works over HDMI.

My problem is now how can I remove and reinstall all sound related packages to get these two options in my installed Ubuntu?

Or is there a guide how to reinstall all these packages?

---

### Post by P4man on 2011-02-01
Undoing what you have done over the past 2 months of experimenting (and perhaps more, since you upgraded from 10.04 and you might have tweaked that to make HDMI work) might be a mission impossible. Easiest is probably just backing up your home folder (or partition), and do a fresh install.

---

### Post by daniel.jays on 2011-02-01
It was a clean Xubuntu 10.10 installation 2 months ago. Just installed ubuntu-desktop and removed xubuntu-desktop and installed ALSA-Snapshots.

Well I tought with this OS I could remove packages including config files and reinstall necessary packages and it you would be as good as new.

This is why I switched to Linux.. to not have to install the OS every 6 months.

Can anyone confirm with the latest kernel update the profile Option "**Digital Stereo (HDMI) Output**" will still be available?

In this case even Windows (and I don't like Windows at all) is far less complicated beside the registry crap. Really disappointing situation..

---

