---
title: "Installation not detecting hdd"
date: 2011-03-21
forum: Installation &amp; Upgrades
---

### Post by J_Wales on 2011-03-21
Ubuntu installer does not detect my sata drive during installation.

Hardware:
Asus p4gv-mx
4gb ram
250gb wd sataII drive
ide cdrom
Bios options tried:
Disabling apci 2.0
disabling apci

setting IDE mode to
       [Enhanced]
       [compatibility] w/both sata only, pata& sata settings
Setting my pata cdrom to slave and plugging it into the slave position of the ide ribbon.

I've tried these combinations with the usb installer, and dvd installer.
I've tried loading the live cd/dvd & usb then running the installer with in.
I've tried the spacebar method, hitting f6 and apci=no, noapci

The live cd has no problems detecting and mounting my hdd, however the installer does not detect it.

I have very limited experience with linux in general, though I have run ubuntu in the past. I am currently downloading the alternative installation cd, if this fixes my issues I will report back. I appreciate any help that anyone here can give me. Thanks!

---

### Post by Hedgehog1 on 2011-03-21
Some ideas:

1) Don't put the IDE CD ROM as slave, make it master.
2) Make a 'LiveUSB' instead of a 'LiveCD', disconnect all IDE devices; then boot from the USB stick.

Turning .iso into LiveUSB link: [usb-linux-tutorials]("http://www.pendrivelinux.com/category/new-usb-linux-tutorials/")


***The Heddge***

:KS

---

### Post by J_Wales on 2011-03-21
Correction, I have a p5gv-mx not a p4gv-mx. I used this link [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download) to download ubuntu and create a bootable usb stick. Is that a live usb?

Anyway i'll try your suggestion when I get home from work. I'm going to re-download it again as well and do the m5checksum to make sure its a good copy.

Thanks Heddge!

---

### Post by J_Wales on 2011-03-23
I did as you directed with no luck. I ran the check sum of the iso before I burned and verify'd the burn using imgburn. Everything is fine, but nither the cd nore the usb install detects my sata drive. I did as other suggested elsewhere and downloaded the alternative cd and it worked fine thought it seemed glitchy and was unsure if it installed correctly. This seem to work fine so far.

It detected my sata as a scsi device, maybe this is normal but scsi is not sata in my book but what do i know it works fine... It also said something about detecting a raid setup, I don't know if it was talking about the generic southbridge raid controllers that most of these manufactures put on boards, or the raid 0 configuration the sata drive was in previously. Anyone have a clue?

anyway... 
Thanks for the help. Just wanted to let everyone know, the alternative iso worked for me. So far I like everything about the new updates in ubuntu besides a few pieces of software that are not supported, or should i say, whose makers do not support linux.

---

