---
title: "BIOS update on laptop with no USB Boot option"
date: 2013-02-23
forum: Installation &amp; Upgrades
---

### Post by Concise Conch on 2013-02-23
So, I have been heavily researching for hours how to overcome my predicament here with no success. I want to upgrade the BIOS on my laptop, the model is a little bit older and theres no USB support whatsoever. It's a Toshiba satellite. From what I gather, outside of replacing the hard drive with a windows based hard drive, my only other possible option is to create a boot disk (CD) that the computer will interpret as a Floppy Disk. I also gather that I am to do this with FreeDos.

 After reading several different articles and help threads I am still very confused. Pretty much everything I read was outdated all the way back to Ubuntu 9.04. I have FreeDos, I have the new BIOS exe file from Toshiba's website and from there I'm pretty much stuck. Most of what I read always includs a step to "burn the _BIOS image_ and the _BIOS Utility_ to the cd." This is one of the especially confusing parts as I don't know how to distinguish between these two files. Before anyone jumps on me for not knowing if I need the BIOS update, yes I need it to configure virtual box to work correctly as it is giving me the "i686" error. Please any advice is appreciated


link to some of my sources:  [http://www.linuxinsight.com/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html](http://www.linuxinsight.com/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html)

[http://www.rom.by/Art_of_BIOS_flashing](http://www.rom.by/Art_of_BIOS_flashing)



link to the bios update file: [http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/modelContent.jsp?ct=DL&os=&category=&moid=1854867&rpn=PSU30U&modelFilter=U305-S7446&selCategory=2756709&selFamily=1073768663](http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/modelContent.jsp?ct=DL&os=&category=&moid=1854867&rpn=PSU30U&modelFilter=U305-S7446&selCategory=2756709&selFamily=1073768663)   (click BIOS in "refine search by" field.)

---

### Post by dino99 on 2013-02-23
from your toshiba link above, the utility is named HWsetup, and the latest bios seems to be from 2009. Looks like the process needs to be run from win7, but not sure, as nothing describe how to update bios for old hardware.

---

### Post by grahammechanical on 2013-02-23
I have never flashed my BIOS. I tell you that so that you do not think that I am speaking from experience. But I would guess that you need both the BIOS utility and the BIOS image on the CD. For, I guess, that you would need the utility you flash the BIOS chip with the image.

The instructions for updating the BIOS of my motherboard by floppy disk are:

Save the BIOS file to a bootable floppy disk and copy the utility from the motherboard support CD to the bootable floppy disk that you created earlier.

I guess that the procedures must be similar. You need to boot into something - floppy, USB - that contains a utility that can save the present BIOS file and over write it with another BIOS file and you need the newer BIOS file.

Regards.

---

### Post by 2F4U on 2013-02-23
From the package description I read:

> WinRAR 32-bit self-extracting ZIP file includes both Windows-based and  diskette based BIOS update installation options.  See the included  documentation for details.

So, you would either need a working installation of Windows or be able to boot from a diskette.

---

### Post by Concise Conch on 2013-02-23
I'm sorry guys in my first post I meant to say I don't have USB Booting support in my current bios. I thought I would be able to handle setting up a "floppy" for the boot but the more I read it just seemed more and more intricate especially after reading all the mistakes people made and results.   grahammechanical, dino99, thanks that clears thinks up enough. Will I really have to use windows7? I have a copy of vista that I think I suppose I could dual boot the system with. There's no real live cd version of windows is there?

---

### Post by ahallubuntu on 2013-02-23
~

---

### Post by Concise Conch on 2013-02-24
Well I'm glad I decided to ask instead of trying it. Yeah I have been wanting to experiment with virtual machines and according my  research on the error I got when I tried to create one, it was most likely a matter of my outdated bios. I figured I might as well kill two snails with one stone and get up to date.

---

