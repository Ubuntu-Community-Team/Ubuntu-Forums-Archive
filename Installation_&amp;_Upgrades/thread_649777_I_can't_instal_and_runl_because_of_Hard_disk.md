---
title: "I can't instal and runl because of Hard disk"
date: 2007-12-25
forum: Installation &amp; Upgrades
---

### Post by vliegje20 on 2007-12-25
Last week i got an old pentium 3 100 mHz 256 mb without hard disk.
I had an 20 GB so I put it in the pc. It must become a test pc for the latest Ubuntu version.
I put the 7.10 alternate cd (burned from .iso) in the drive. Then i get some option and coosed install. The word UBUNTU with a loading screen comes up, the screen turns black

(initramfs) [55.612197] ata 1.00 exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen

This was with self burned 7.10 and 7.04 both Ubuntu alternate and desktop cd. Ubuntu 6.06 desktop which i ordered at Ship-It worked and installed correctly

The i put a burner in the system same fault. Also switched memory same fault. Then i put a 80 gb hard disk in and the problems were over. I don't want to use the 80 gb because there are still many documents and files on. 

I checked with UBCD the 20 gb hard disk its said that there was no error found. Is there a way to still use the 20 gb with 7.10 and the alpha of 8.04?

---

### Post by logos34 on 2007-12-25
maybe it was choking on hardware detection--are you sure the 20 gig is jumpered correctly?  Is it being recognized in the Bios?

---

### Post by vliegje20 on 2007-12-26
I tried 2 different jumper settings:
- master
- cable select
On both ways i get problems

Also the harddisk is recognized in the bios. Otherwise i can't have 6.06 installed.

---

### Post by logos34 on 2007-12-26
sorry, didn't read your question carefully the first time.

try adding some [kernel parameters]("https://help.ubuntu.com/community/BootOptions").

irqpoll

noapic,nolapic

---

### Post by vliegje20 on 2007-12-27
Thanks, i tried some things out last night. But somethings weren't clear to me. 

I now have a 8.04 alpha desktop cd burned. When I push F6 i get a line.
The link you gave said: 
boot: /boot/vmlinuz-2.6.15-26-k7 root=/dev/hda1 ro quiet splash

i see a different line but also i dont know the kernel. When i hit enter i boots directly. I get the following error:
kernelpanic. - not syncing VFS: unable to mount root fs on unknownblock (8,1)

---

### Post by logos34 on 2007-12-27
The line in the link I gave you is just an example--you add the options in the F6 box to the END of the kernel line, (after '...quiet, splash...').  8.04 is probably using kernel 2.6.23... something or other

---

### Post by ImALittleTeaPot on 2007-12-27
Many people have been getting similar messages when installing because of a kernel bug that affects IDE systems. What kind of hard drives are you using, and what are your BIOS settings on them.

---

