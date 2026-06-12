---
title: "Upgrading BIOS with FreeDos"
date: 2013-09-03
forum: Installation &amp; Upgrades
---

### Post by petterip2 on 2013-09-03
Hi,

I have been trying to upgrade the BIOS for my HP Envy laptop last weeks and I am not advancing. The task and concepts are too difficult for me and I have a hard time understanding articles related to this. I tried installing Freedos with VirtualBox, but then I read that for the bios upgrade it was a wrong approach to start with. However, during this I learned that the bios upgrade package that HP provides can not be run in "DOS mode", which means that the HP bios .exe can only be executed in Windows.

So, I am now trying to create a bootable Freedos USB or a CD, but the problem is that HP package does not fit in the Freedos image. Now my question is that can someone figure out from the HP package which files are actually needed for upgrading the bios? I mean, do I really need _all_ the files that are included in the HP package? If so, then I guess it is no-go for FreeDos due to the above reasons.

The HP bios package is a .exe archive available at:
[URL="http://h10025.www1.hp.com/ewfrf/wc/softwareCategory?os=4063&lc=en&cc=us&dlc=en&sw_lang=&product=5144736#N858"]http://h10025.www1.hp.com/ewfrf/wc/softwareCategory?os=4063&lc=en&cc=us&dlc=en&sw_lang=&product=5144736#N858
[/URL]
Once sp60715.exe is extracted it contains the following files:
03385.fd
AtpTimerInfo.dll
Ding.wav
FlsHookDll.dll
FlsHook.exe
FWUpdLcl.exe
InsydeFlash.exe
iscflash.dll
iscflash.sys
iscflashx64.sys
platform.ini
xerces-c_2_7.dll


The instructions that I am using for the BIOS upgrade  are:
[URL="http://ubuntuforums.org/archive/index.php/t-318789.html"]http://www.linuxinsight.com/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html
[/URL]
[URL="http://ubuntuforums.org/archive/index.php/t-318789.html"]http://ubuntuforums.org/archive/index.php/t-318789.html
[/URL]

---

### Post by tgalati4 on 2013-09-03
I upgraded my Acer Extensa by making a Fat32 partition, installing a FreeDOS to it and adding the appropriate GRUB entries.  Once booted into FreeDOS, you can load the self-extracting flashing package and then run the installer.  You just need a large enough partition to hold both the zipped (sp60715.exe) file and its unzipped contents.  There are some tutorials to do this, but I don't have the links handy on this machine.

---

### Post by petterip2 on 2013-09-05
I think the partion might not solve the the problem that the HP BIOS package won't run in DOS mode. It is a Windows program and to my knowledge can not be executed in FreeDos (?).

---

### Post by grahammechanical on 2013-09-05
The recommenadtion not to use DOS Mode may simply mean that Windows should not be running when an attempt is made to flash the BIOS. It does not necessarily mean that the exe file will not run in DOS or an alternative DOS. If I remember back to my younger days, DOS programs were also exe files.

I would suggest that it is best to follow the manufacturer's instructions. Things can go wrong with flashing the BIOS. Does the machine come with a motherboard manual or a CD with drivers and other stuff?

My motherboard came with such stuff. There was even a Windows utility for flashing the BIOS. I do not have Windows so I cannot use it but I also noticed that there were utilities for flashing the BIOS from a bootable floppy. And also advice for flashing the BIOS using other methods.

Regards.

---

### Post by petterip2 on 2013-09-06
> **grahammechanical said:**
> The recommenadtion not to use DOS Mode may simply mean that Windows should not be running when an attempt is made to flash the BIOS. It does not necessarily mean that the exe file will not run in DOS or an alternative DOS. If I remember back to my younger days, DOS programs were also exe files.

Hmm, it's not a recommendation. To my knowledge Windows programs just don't run in DOS although they end with .exe. I tried running the sp60715.exe in a VirtualBox Freedos and it stops in "This program cannot be run in DOS mode" error.

Hence, the dilemma that I face is should I go thru the all trouble of trying to install Freedos in a partion or USB or CD or whatever if in the end I still can not execute that BIOS upgrade program provided by HP. The other option is re-installing entire Windows just to get a bios update, which is very disappointing.

---

### Post by ubfan1 on 2013-09-06
I had a similar problem with my old HP laptop which got a motherboard replacement.  Failed to get the program running on any DOS image I had around, so finally put in the old Windows disk, just for the flash.  You might try some of the Windows USBs I see reference to, they might be sufficient.

---

### Post by exodus_ on 2013-09-06
May I ask what you're flashing your BIOS for?  Depending on what it is, you might not even really need to flash it at all.  Flashing the BIOS can be pretty risky if you don't understand what's going on.

---

### Post by mikewhatever on 2013-09-07
> **exodus_ said:**
> May I ask what you're flashing your BIOS for?  Depending on what it is, you might not even really need to flash it at all.  Flashing the BIOS can be pretty risky if you don't understand what's going on.

+1. It sounds like a major waist of time, especially since the .exe won't work in DOS. 
On the second thought, perhaps it's a thingly camouflaged attempt to brick the machine.

---

### Post by tgalati4 on 2013-09-07
It looks like you have no choice but to find a slim version of Windows to install on the machine, run the BIOS flasher in Windows, reboot and check the BIOS to make sure it is the latest version, then wipe the machine and install your distro of choice.  A pain to be sure.

I've used freedos to flash Dell, IBM, and Acer machines, but don't have any HP's at the moment.

---

### Post by petterip2 on 2013-09-08
The reason I want to updgrade the BIOS is just to get the latest fixes to it. This HP Envy machine has some issues with fan control and some other defects that might be fixed in the new bios. I have also ran into a possible kernel bug, but before it is investigated any further the bios needs to updgarded to the latest:
[URL="https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1173741"]https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1173741
[/URL]
Anyhow, it is certainly a good question if all this is worth it. Needing to install windows and ubuntu again is something I or anyone really don't feel like doing...

I was kind of hoping there would be an easier option - if, as example, some of the .exe files inside the sp60715.exe package could be executed in FreeDos and if they would be sufficient to upgrade the bios. I assume that most of the Windows related stuff in the package is just a GUI warnings for average Windows users. Or the file that ends with .fd extension, which after some small googling has something important to do with the bios image.

Thanks for all the help - I need to think hard before making up my mind...

---

### Post by prodigy_ on 2013-09-08
Actually you can make a Winodws PE CD under Linux: [https://wiki.archlinux.org/index.php/Windows_PE](https://wiki.archlinux.org/index.php/Windows_PE)
Just don't forget to add BIOS upgrade files to the ISO.

Note: if you see multiple updates for your model on HP site, d/l them all and add them all to the ISO. Yes, they can be non-cumulative so you might need to flash them sequentially. That's HP for ya.

---

### Post by petterip2 on 2013-09-10
Wow. This looks promising and I'll definately investigate it... Thanks.

One question, from the outset it appears as PE has support for networking. If so, then could I just download the HP bios updates from within PE instead of adding them to the iso image?

---

