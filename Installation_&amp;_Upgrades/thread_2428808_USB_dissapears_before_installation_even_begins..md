---
title: "USB dissapears before installation even begins."
date: 2019-10-09
forum: Installation &amp; Upgrades
---

### Post by thesheepguy on 2019-10-09
SOLUTION: Update BIOS firmware. Apparently Ryzen 2 and 3 processors have issues with outdated firmware. 

After I select the "install" option when the computer boots from the USB, it takes a minute or so, and then the error ```
(initramfs) Unable to find a medium containing a live file system.
``` appears. I have tried all of the methods listen on various forums, I'll briefly explain what I've done so far:
[LIST]
[*]Plug the USB out and back in during the installation when it's trying to find the medium. 
[*]Plug the USB in a USB 2, USB 3, USB Hub, front ports, back ports, or any other kind of port. No matter where I stuck it in to, the same error occured. 
[*]Use a different USB. Both, a USB 3 32 GB and a USB 2 2 GB stick have both failed. 
[*]Change various BIOS UEFI settings (Legacy USB Support, XHCI hand-off, and emulating the stick as an HDD or a CD-ROM). 
[*]Try another machine - my laptop can run it find, so it's definitely not the USB stick's, the ISO image, or the copying process' fault. 
[*]Enable, and disable secure boot, have PR keys that are pre-defined, default, or none; specify Windows in the OS option for secure boot, specify "other OS", both seemingly doing nothing (especially considering I use the "other OS" option for my Windows installation anyway). 
[*]Disconnect all unnecessary devices. It made no difference whether my mouse, webcam, microphone, two other hard drives, or USB WiFi stick were plugged in or not. 
[*]Used various launch options such as noacpi, and nomodeset. 
[/LIST]

I'm trying to install Ubuntu 19.04 x64, and my computer specifications are:

[LIST]
[*]CPU: AMD Ryzen 3 2200G (4 core @ 3.5 GHz) 
[*]GPU: AMD Radeon R9 380X 
[*]RAM: 8 GB DDR4 
[*]Motherboard: ASUS PRIME B450M-A 
[/LIST]

 
I've posted this on the [Manjaro]("https://forum.manjaro.org/t/live-boot-usb-doesnt-start-to-desktop/106278/") and [Debian]("http://forums.debian.net/viewtopic.php?f=17&t=143918") forums, since I've tried this on those two distros as well, without any help. I've run of things to look up, and I'm about to sadly give up. Hopefully I'll get some more support from this forum than the others!

---

### Post by #&amp;thj^% on 2019-10-09
This may end like the other methods youv'e tried, but add this to the launch option.
Just before "quiet" add this,"acpi_osi='Windows 2018"
```
acpi_osi='Windows 2018'
```[SIZE=4][/SIZE]
And are you trying to install Ubuntu to the same hard drive Windows is on?

---

### Post by thesheepguy on 2019-10-09
I have two hard drives, one has Windows 10 on it, 500 GB SSD, one has a blank FAT32 that I'll override during installation, when I actually get there :P

The first time I did what you asked, I [got a colourful screen]("https://i.imgur.com/2oYprpv.jpg"), then the computer froze on that. By disabling the quiet parameter, I [got this]("https://i.imgur.com/tONJlBl.jpg"). So unfortunately, not the solution.

---

### Post by ubfan1 on 2019-10-09
Is your motherboard's firmware up-to-date?  That helps a lot for the Ryzen 2 series as well as the Ryzen 3s.

---

### Post by thesheepguy on 2019-10-10
Thank you, that's exactly what issue is, after installing the 1820 version of the firmware it works!

---

