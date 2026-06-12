---
title: "GRUB loader, Error 21"
date: 2005-02-23
forum: Installation &amp; Upgrades
---

### Post by gappy on 2005-02-23
I have installed Ubuntu on an old T20, and loved it. I have a T40p with an original IBM 40GB external USB2 Drive, and today I tried to install Ubuntu 4.10 on this disk. The installer correctly saw the disk and installed on it. But, when it asked to restart the machine, it gave me the following message:
[B]
[FONT=Courier New]GRUB Loading stage1.5.
GRUB loading, please wait...
Error 21
[/FONT][/B]

I have looked around, and this seems a problem with the BIOS not recognizing the external HD (strange, though). Does anyone now how to fix the problem, possibly with the liveCD? Thanks,

gappy

---

### Post by bored2k on 2005-02-23
[QUOTE=gappy]I have installed Ubuntu on an old T20, and loved it. I have a T40p with an original IBM 40GB external USB2 Drive, and today I tried to install Ubuntu 4.10 on this disk. The installer correctly saw the disk and installed on it. But, when it asked to restart the machine, it gave me the following message:
[B]
[FONT=Courier New]GRUB Loading stage1.5.
GRUB loading, please wait...
Error 21
[/FONT][/B]

I have looked around, and this seems a problem with the BIOS not recognizing the external HD (strange, though). Does anyone now how to fix the problem, possibly with the liveCD? Thanks,

gappy[/QUOTE]

i hav had installation problems b4 , i would usually delete the MBR with a tool-disc like Hiren's or whatever ] or get stand alone mbr tools [ and then reinstall grub with the closest live cd on hand ....

[http://www.ubuntuforums.org/showthread.php?t=16263](http://www.ubuntuforums.org/showthread.php?t=16263) check the 3rd post for help on this !

---

### Post by wallijonn on 2005-02-23
A GRUB error 21 usually indicates that it cannot read the HD format. In your case, do you have the latest BIOS version installed? Usually error 21's are solved by changing the HD type in the BIOS. Obviously this cannot be done with external USB devices. So there must be some way to tell GRUB to load a USB driver before speaking to the HD (like SATA drives). I wish I could have been of more help, but I'm afraid that those with laptops will have to come to your rescue.

---

