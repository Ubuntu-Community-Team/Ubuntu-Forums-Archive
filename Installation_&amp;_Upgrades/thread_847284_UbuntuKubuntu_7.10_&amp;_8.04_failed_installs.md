---
title: "Ubuntu/Kubuntu 7.10 &amp; 8.04 failed installs"
date: 2008-07-02
forum: Installation &amp; Upgrades
---

### Post by mschifter on 2008-07-02
Hi,

I've been trying to get an install working off the Live CDs of all 4 variants mentioned in the Title. The only luck I've had is doing a Live run under Ubuntu 7.10. I've got a Dell Vostro 400 which has been reportedly associated with bug #223088, which is essentially the problem I've experienced.

The following few paragraphs is regarding 7.10, which I've had better results from:

After researching this quite a bit on the internet, I am guessing this is all driver-related. I've got an nVidia 8300 GS, which is supported under the latest nvidia-glx-new driver. I can boot under the VESA driver just fine from the Live CD (though without network support). 

However, booting off the hard drive with the standard boot, I get most of the way through the boot and X starts up and I get a double-headed signal off the graphics card, but just a black screen with a small round cursor (which remains live via the mouse).

In recovery mode off the disk, I can startx at the bash prompt and it starts just fine (though without network support).

I'm thinking the problem is either with the graphics driver or with the network driver, but I can't seem to narrow it down for sure. I've tried Ctrl+Alt+F1/F2 but this doesn't really work after I'm in X. In recovery mode, I can Ctrl-Alt-Backspace to the text prompt.

I've tried in recovery mode to use the VESA driver and nVidia, but no suggestions here have helped to get the standard boot to run right. At best, I get an alternating display between text and X startup 6 times until failure.

Here's what I get from 8.04 installs upon boot:

[<timestamp>] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[<timestamp>] ata2.00: cmd a0/00:00:00:24:00/00:00:00:00:00/a0 tag 0 pio 36 in
[<timestamp>] ata2.00: status: { DRDY }

This repeats every few seconds. I don't get this under 7.10.

I saw advice to download, build, and install my ethernet driver, which makes sense. I have the driver downloaded under windows, but I can't get it to the linux partition. After all, I can only boot linux successfully under recovery mode. I am unable to reach the windows partition under that mode. Same goes for the linux partition under windows, of course, and live mode doesn't help here. So there's no way for me to build the right driver and install it.

Per the graphics driver, if I can get a normal boot going under my dual boot partition, I'm sure I can get Envy or aptitude to install the nvidia package.

Any help would be appreciated.

Matt

---

### Post by tech0007 on 2008-07-02
boot to recovery, add 'vesa' to your xorg.conf file. that should give you the gui in normal mode. you can also mount your windows partition while in recovery. look at the output of 'sudo fdisk -l /dev/sda' boot to normal mode. then use the mount command.

---

