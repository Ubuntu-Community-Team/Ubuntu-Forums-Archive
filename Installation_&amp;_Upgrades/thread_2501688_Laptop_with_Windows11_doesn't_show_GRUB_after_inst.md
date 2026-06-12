---
title: "Laptop with Windows11 doesn't show GRUB after installation of Ubuntu 24.04"
date: 2024-10-17
forum: Installation &amp; Upgrades
---

### Post by melgosin on 2024-10-17
My laptop: MSI Thin 15 B13VE, 512 Gb hard disk. 

I tried installing Ubuntu 24.04 on my laptop with Windows 11 preinstalled and initially everything seemed to be fine. 

When the installation finished, upon reboot the Grub did not appear and it entered Windows. The system showed an alert and the Ubuntu partition/partitions were (apparently) gone. The space appeared as a single partition.
I did some research and saw that it was necessary to disable Secure Boot, so I did. I tried to install again this time manually by assigning each of the partitions manually. Same result.

I know Ubuntu is there because I can see the partitions from Windows but I guess there is some problem with the boot loader that does not allow Grub or the Windows menu to be displayed (which I don't remember what it's called).

I'm a bit desperate and my knowledge is quite limited (especially in Linux). Can you give me a hand?

I would like to have Ubuntu as the primary operating system and Windows as the secondary one, in case it is relevant.

Thank you very much in advance

---

### Post by grahammechanical on 2024-10-17
I do not use Windows. I understand that Windows fast startup must be turned off. You should be able to use the UEFI to boot Ubuntu. When you are in Ubuntu run in the Terminal

```
sudo update-grub
```

Watch the printout to see if the boot loader (Grub = GRand Unified Bootloader) detects the Windows bootloader files.

Regards

---

### Post by oldfred on 2024-10-17
Boot Ubuntu live installer in live mode & use terminal to install Boot-Repair ppa. The report will give us lots of info on your configuration and what may need fixing.

Please copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed. Use often updated ppa version with your USB installer or any working install over somewhat older ISO. 
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by melgosin on 2024-10-25
Thanks for the advice. I finally found the problem. 

The thing is that I didn't know that in the new BIOS/UEFI (new for me at least) besides being able to select the boot order of the hard drives, there is also a section to select the priority in the boot sequence when there is more than one OS on the same hard drive. My mistake, sorry.

I hope at least that if someone has the same problem as me they will read this and find the solution more easily.

I add a couple of pictures of the menus in the BIOS.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=294418&stc=1[/IMG]

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=294419&stc=1[/IMG]
[IMG]https://photos.app.goo.gl/41jAw4QzCTNMBbCx7[/IMG]

[IMG]https://photos.app.goo.gl/2Z2kGK98GLPpKfdd8[/IMG]Regards

---

### Post by ubfan1 on 2024-10-25
The MSI boot order with USB first may be overridden in the UEFI hard disk drive priorities. e.g. an SSD in a USB3 enclosure needs to be first in the UEFI hard disk order to be the first boot item, simply having USB first in the primary order is not enough.

---

