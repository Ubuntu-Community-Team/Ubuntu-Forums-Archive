---
title: "Installing Kubuntu to SD card on EeePC 4G"
date: 2009-12-18
forum: Installation &amp; Upgrades
---

### Post by garryknight on 2009-12-18
I run Kubuntu 9.10 on my PC and want to try it on my EeePC 4G. The EeePC has the default Xandros Linux installed and I don't want to nuke that until I know that Kubuntu is going to run ok, so I decided to test it out by installing it onto an 8 GB SD card.

I have the Kubuntu live CD so I decided to boot to the desktop and install from there. Unfortunately, the installation dialog is so large that I can't see the buttons at the bottom. So I plugged in my external monitor and rebooted. Things were looking good at first but then about halfway through the boot process, the external monitor lost the picture, so I was back to square one after two attempts.

Luckily, I have the Kubuntu 9.04 live CD so I started again. This time, I got all the way to the desktop with the display on both the internal and the external monitor. By setting the external monitor to 1024x768, I was able to work my way through the installation, choosing to format the entire SD card as a single ext4 partition. The partitioner started to format the partition but stalled at 0%. So I formatted the SD card on my PC and started a fourth attempt at installation.

The installation began, but the dialog has been showing "Copying files... 22%" for over an hour now.

That 9.10 turned off the external display during boot seems like a bug to me. But I'm not so sure about the stalling while copying files. Either there's something wrong with the SD card (it's been working perfectly until now), or a bug in the installer (unlikely as I installed 9.04 to my PC before upgrading online to 9.10), or for some reason the files aren't being written to the disk.

If anyone can give any input on this I'd be extremely grateful. I'd really like to get Kubuntu running on my EeePC eventually, but if I can't even get it onto the SD card I'm concerned about risking installing it to the onboard SSD storage.

---

