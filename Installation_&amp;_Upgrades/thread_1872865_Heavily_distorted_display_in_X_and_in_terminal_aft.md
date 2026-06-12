---
title: "Heavily distorted display in X and in terminal after install"
date: 2011-10-31
forum: Installation &amp; Upgrades
---

### Post by The last Bert on 2011-10-31
Hi,

I just installed the latest kubuntu on my HP Pavilion dv6552ea laptop. The install process worked fine (from the alternate installer CD), but once the install is complete and the operating system boots, the display is badly distorted and flickering. Switching to a terminal using Ctrl_Alt_F1 does not help, this is just as flickery and distorted, and I am unable to properly read results of any commands I type, so editing config files is out of the question. My understanding is that the terminal no longer runs in text only mode, so must still be using the frame buffer.

Is this fixable? I don't see Grub at startup, but not sure if the correct key press at the correct time would allow me to change some parameters to boot in to text only mode and try and fix this. Alternatively I could try apt-get install open-sshserver from my barely readable terminal, then fix this remotely. The problem is, I'm not sure what to try even if I can get a sensible terminal up. Is this a problem with nouveau?

I believe the graphics chipset is a Nvidia Geforce 7150M.

Thanks very much for any help, I haven't used Linux for quite a few years!

The Last Bert

---

### Post by The last Bert on 2011-10-31
Fixed. For those who experience a similar problem:

1.Hit shift after you see the bios screen to get the Grub2 menu, hit e to edit the boot command and add the option 'nomodeset' after the words 'quiet splash'. Press Ctrl-X to boot.
2.I was then able to see X and terminals at an awful resolution. From a terminal I did a sudo apt-get install nvidia-current, and just for good measure a sudo apt-get --purge remove xserver-xorg-video-nouveau. I think this second step is unnecessary though, I was just angry at nouveau :)
3.Reboot and you should be greeted with a snazzy looking desktop.

the last bert

---

### Post by MAFoElffen on 2011-10-31
> **The last Bert said:**
> Fixed. For those who experience a similar problem:

1.Hit shift after you see the bios screen to get the Grub2 menu, hit e to edit the boot command and add the option 'nomodeset' after the words 'quiet splash'. Press Ctrl-X to boot.
2.I was then able to see X and terminals at an awful resolution. From a terminal I did a sudo apt-get install nvidia-current, and just for good measure a sudo apt-get --purge remove xserver-xorg-video-nouveau. I think this second step is unnecessary though, I was just angry at nouveau :)
3.Reboot and you should be greeted with a snazzy looking desktop.

the last bert
Which means that you had to install "your" video driver... Nomodeset turns off the KMS and Nouveau... temporarily so you can install those.

EDIT-- Summary- This is going to be needed for both NVidia and ATI cards on a new install.  On dist-upgrades, this may be happen and need to be reinstalled, as the old drivers may need to be updated for the newer system. (If binaries)

---

