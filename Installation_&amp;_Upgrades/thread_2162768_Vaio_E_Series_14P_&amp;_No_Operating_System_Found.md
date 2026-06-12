---
title: "Vaio E Series 14P &amp; No Operating System Found"
date: 2013-07-15
forum: Installation &amp; Upgrades
---

### Post by illuminosity on 2013-07-15
Hey guys,

Been having problems getting ubuntu 13.04 working on my new Vaio laptrop for work. I disabled secure boot in the bios, and I've tried installing and booting in both UEFI and Legacy BIOS modes. No luck either way. I've googled around a little, tried using boot-repair and manually changing partitions on a reinstall to ensure the EFI partition is the right size and location, and still No Operating System Found.

I've run out of ideas as to how to get this damn thing working., Does anyone have any ideas on how I can fix this?

Boot Info Script: [http://paste.ubuntu.com/5879308/](http://paste.ubuntu.com/5879308/)

Thanks a lot!

---

### Post by theDaveTheRave on 2013-07-16
illuminosity,

are you trying to boot from alive CD, or trying to boot from a fresh install ?

I know seems like a silly question, so I appologise in advance.

If you are trying to boot from a live CD (with the intention of installing from that), have you checked the BIOS to enable it to boot from the CD as it's first option.

I had an old laptop that didn't like booting from the CD if the HDD was enabled in the boot list, so had to dissable boot from the HDD also, this then meant I had to re-enter the bios to turn off the CD booting and enable the HDD only.

I've had similar problems installing from USB and SD.

Second thought: there now seems to be some nonesense where the boot option are available in 2 locations when you start the pc.
When you first turn on and press F2 (or whatever you need to enter the BIOS) you are presented with the boot order option, then you can get to the BIOS after.
This seems to be a new thing, and doesn't seem to work correctly (in my experience).

David.

---

### Post by illuminosity on 2013-07-16
Thanks for the reply, David. I'm working off a live CD boot now and  that's fine. Just when I remove the live CD, and it tries the hard drive  instead (order is usb, cd, hdd), it doesn't detect the OS. However, if  you go to install again, Ubuntu sees it there, the files are all in  place. I suspect this UEFI laptop BIOS is particularly finicky about how  things are set up.

---

### Post by theDaveTheRave on 2013-07-17
illuminosity,

be sure to remove the usb and cd options from the boot device list in the BIOS, this may solve your problem.

Have you created a 'dual boot' on this system?

Times gone by you could tell a system to boot to a floppy and then use this to select the OS you wanted.

Search through the forums for updating the 'boot partition' and 'GRUB' (which loads the screen to select the desired OS on boot up).

Otherwise you may need to download a new copy of Ubuntu and burn it to CD and start again as a fresh install, remember to check the md5sum of the disk prior to using it to install. It may be that your disk / image has a minor bug in it related to your architecture?

If all else continues to fail, try a different distro, if you want to stay with an ubuntu flavour you could go for Mint, debian, bodhi... or a host of others.

David

---

