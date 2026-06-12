---
title: "Ubuntu does not show up in boot menu in BIOS"
date: 2013-11-04
forum: Installation &amp; Upgrades
---

### Post by axelsword on 2013-11-04
Hello!

The HDD with Ubuntu 12.4.3 LTS 64-bit version is not displayed in boot menu in BIOS. Can this be solved?

When I insert the install DVD the ubuntu setup detects the previous installation. The HDD is displayed under "advanced" in BIOS.

The only HDD  connected to laptop ASUS G75VW is SSD Samsung 840 Pro (256 gb). Ubuntu installation was successful.

Any help would be appreciated. There is the option to add a boot file (path to it and other stuff too complicated for me).

---

### Post by grahammechanical on 2013-11-04
How do you know that the Ubuntu installation was successful? Can you load into it? I have two hard disks and the BIOS does give me options to select which HHD to boot from but it makes no mention of Ubuntu at all. I have several installations of Ubuntu and both HHDs have a Grub boot menu installed in the MBR. So, whichever HHD I boot with I get a Grub boot menu that lists all my various Ubuntu installations. I wonder if we have the same understanding of the term BIOS. I wonder if you have the UEFI boot system. Do you have any other OS on that machine?

---

### Post by fantab on 2013-11-04
If you believe that you install was successful then try [**Boot-Repair**]("https://help.ubuntu.com/community/Boot-Repair#A2nd_option_:_install_Boot-Repair_in_Ubuntu") using Ubuntu DVD. It should fix if there are any boot-loader issues. If not, then post the LINK to the BootInfo-Summary that Boot-repair generates here.

---

### Post by axelsword on 2013-11-04
Ohh, thank you, fantab!

Boot-repair worked like a charm. Now I can use ubuntu. It's lightning fast from SSD.

How do I mark this thread as "solved" ? *Edit* found it. Thanks!

---

