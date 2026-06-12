---
title: "Monitor Shuts Off During Installation"
date: 2010-10-17
forum: Installation &amp; Upgrades
---

### Post by Goveynetcom on 2010-10-17
So I decided to download and install Xubuntu on my other desktop. So I downloaded the Xubuntu 10.10 iso, used the USB Start Disk creator on my other Xubuntu desktop, and made a bootable flash drive.
So, I plug it in, and it boots with the select a boot option and I choose Try Xubuntu without installing.
The screen flashes, the blinking underscore shows up, then the monitor just shuts off. I thought okay, maybe it's just turning of because the OS is still booting. I came back 5-7 min later, shook the mouse, pressed the arrow keys on the keyboard, the monitor still didn't turn on.
So the second time, I chose Install Xubuntu, same issue. I tried test memory, same issue.

So I'm not sure what to do now...
I might download the Ubuntu 10.10 iso, and see if that works, but I already had this one ready, so I am looking for help.
Thank you,
Goveynetcom.

---

### Post by efflandt on 2010-10-17
Which Xubuntu was your other PC, because maybe its Startup Disk Creator does not know how to handle the new syslinux of 10.10 yet.  The following was from known issues while Maverick was under development:

Maverick  thumb drive images built on Lucid (& earlier?) fail to  boot due to  differences in syslinux version - the 'ui' keyword in the  syslinux.cfg  file needs to be removed to get it to boot.  A fix for  this on Lucid is  available to be applied, see lucid-updates. ([608382]("https://bugs.launchpad.net/bugs/608382"))

But many people seem to have blank screen issues with 10.10.  What video card/chip do you have?  Do you have any older Ubuntu versions that boot on that machine (older CD's or anything or does 10.04 boot from that USB)?

---

### Post by oldfred on 2010-10-17
Mine was Ubuntu but I think the installer is the same.

I have nvidia and my monitor went to standby & had to do this:
boot from the cd, press anykey then F6 and then select the nomodeset option.
(I acutally edited my grub.cfg as I use grub2 to directly boot ISO on USB, or edit in USB's syslinux.cfg or text.cfg as in first boot)
then
On first boot after install, press e on getting the GRUB bootloader menu.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

After I installed nvidia driver (default from pop up) then it has worked without issue.
Or it should be in System>administration>Hardware drivers.
Possible additional things to run once nvidia working:
gksudo nvidia-settings
sudo nvidia-xconfig

[http://pricklytech.wordpress.com/2010/07/31/ubuntu-10-4-lucid-black-blank-screen-during-installation-live-cd/](http://pricklytech.wordpress.com/2010/07/31/ubuntu-10-4-lucid-black-blank-screen-during-installation-live-cd/)
[https://wiki.ubuntu.com/X/Troubleshooting/Nouveau](https://wiki.ubuntu.com/X/Troubleshooting/Nouveau)
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by Goveynetcom on 2010-10-18
> **oldfred said:**
> Mine was Ubuntu but I think the installer is the same.

I have nvidia and my monitor went to standby & had to do this:
boot from the cd, press anykey then F6 and then select the nomodeset option.
(I acutally edited my grub.cfg as I use grub2 to directly boot ISO on USB, or edit in USB's syslinux.cfg or text.cfg as in first boot)
then
On first boot after install, press e on getting the GRUB bootloader menu.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

After I installed nvidia driver (default from pop up) then it has worked without issue.
Or it should be in System>administration>Hardware drivers.
Possible additional things to run once nvidia working:
gksudo nvidia-settings
sudo nvidia-xconfig

[http://pricklytech.wordpress.com/2010/07/31/ubuntu-10-4-lucid-black-blank-screen-during-installation-live-cd/](http://pricklytech.wordpress.com/2010/07/31/ubuntu-10-4-lucid-black-blank-screen-during-installation-live-cd/)
[https://wiki.ubuntu.com/X/Troubleshooting/Nouveau](https://wiki.ubuntu.com/X/Troubleshooting/Nouveau)
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
I'll have to try that when I can get access to my PC again. Sounds like the problem I am probably having.

@efflandt
Well the other Xubuntu Machine is running 10.04. I have tried a Ubuntu 9.04 and 9.10 CD I had, and it booted and installed fine. I believe my VC is an Nvidia GeForce 6150 LE if that helps.

---

### Post by Goveynetcom on 2010-10-19
Yeah that seemed to work, thanks :popcorn:.
It detected my card had proprietary drivers, only prob is that I can't hook this computer up to my network yet >.<
I have to get ndiswrapper working.
But hopefully I can just locate the .deb package on the server and transfer it offline.
Hopefully no other problems arise, thanks guys :).

---

