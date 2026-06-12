---
title: "cannot install Ubuntu 11.10 onto Corsair SSD"
date: 2011-12-24
forum: Installation &amp; Upgrades
---

### Post by annbo812 on 2011-12-24
Hi,

i am trying to install Ubuntu 11.10 onto the new Corsair SSD Force 3 60 GB.

The Installer has some difficulties recognizing the device, but even when it does see the SSD and starts the installation process, it freezes at some point.

Syslog says: 

 ubuntu kernel:  [...] ata3.00: failed to read native max address (err_mask=0x4) and
[...]
 ubuntu kernel:  [...] ata3.00: failed command: IDENTIFY DEVICE

I made sure that BIOS sees the device, I also tried first to create partition on the SSD with gparted and then to install Ubuntu onto it - without any result. Fedora Installation also failed. However, Windows did not have any problems with installation at all.

What goes wrong with Ubuntu?

---

### Post by 2F4U on 2011-12-24
What sata mode do you set in BIOS, AHCI or IDE?

---

### Post by annbo812 on 2011-12-25
I set IDE. and I do not have ACHI as an option, i can chose only between IDE and RAID. And when I chose RAID, BIOS does not see SATA discs

---

### Post by darkod on 2011-12-25
Strange, look more carefully in the bios. Boards from 4 years ago have AHCI option.

Some of the SSDs have problems running in IDE, especially it seems with linux. Also, using a SSD in IDE is limiting the features, you should really use it in AHCI mode.

---

### Post by annbo812 on 2011-12-25
is there any possibility to enable AHCI mode on the ASRock N68-S3 UCC board with AMD Athlon II X2 250?

---

### Post by darkod on 2011-12-25
Unfortunately according to the manual at the Asrock website, the only options are IDE and RAID.
I don't know what to recommend.
I remember few days ago another person had similar problems with the install on a SSD and it worked right away after changing from IDE to AHCI. But in your case you don't have AHCI on that board.

---

### Post by annbo812 on 2011-12-25
thank you for your help, at least i know where the problem seems to be

---

