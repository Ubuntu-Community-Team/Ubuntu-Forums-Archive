---
title: "New installation and double boot"
date: 2019-04-25
forum: Installation &amp; Upgrades
---

### Post by ludovictheate on 2019-04-25
Hi,

I recently purchased a new desktop with windows 10 installed on it. I have one SSD and one HDD. I prepared an Ubuntu USB drive and have resized the windows 10 partition (following some tutorial on the net). I have then booted on the USB drive and installed Ubuntu. However the option "Install alongside Windows 10" did not appear and I had to used the manual mode. Since then, I am not able to boot using the Ubuntu partition and I always end up with booting into Windows 10. 

A few more information:
[LIST]
[*]System info says Bios Mode = UEFI. I have tried to change it via the "MSI click bios" to "UEFI + Legacy", but if I do that, I end up with GRUB telling me "error: unknown filesystem" so I reverted to UEFI
[*]Here is a screenshot from Disk Management: [ATTACH=CONFIG]283103[/ATTACH]
[/LIST]

I have no clue what I should do to fix this problem. Would you have any idea ? Thanks.

---

### Post by yancek on 2019-04-25
I imagine your current problems would have been prevented if you had  read the Ubuntu documentation before trying to install, see the link  below.

 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

You  indicate that on your computer, you have an SSD and a HDD but neglected  to mention on which you have windows or on which you tried to install  Ubuntu?  It appears you have both on the 465GB partition, is that your intentions?
Reading the Ubuntu documentation at the link above, you will see that it is necessary to turn off fastboot/hibernation before installing Linux.  The reason microsoft uses fastboot is so that that the system will boot in less than 3 minutes and hibernation/fastboot are defaults on windows.  No Linux system will mount a hibernated system due to the risk of damage to the filesystem.  That is the first thing I would suggest and might be why windows wasn't seen and you were not given the Install Alongside option.  The manual/Something Else option is better as it gives the user control so that s/he know what happens in the install in the case that something goes wrong.  Notes help with that also.

When reading the link above, note that if windows is installed on a GPT disk  then you need a UEFI install.  You would need to also install Ubuntu UEFI in order to boot windows. 

Might be best to get boot repair from the site below.  You can use the Ubuntu install media.  Select the 2nd option to download the ppa version as explained at the site and after it is downloaded, run it and select ONLY the option to Create BootInfo Summary.  When that finishes, you will get a link which you can post here and someone should be able to help.

---

### Post by ludovictheate on 2019-04-25
Thanks.

I am trying to install both Windows and Ubuntu on the SSD, so indeed both on the 654Gb partition.

I forgot to mention it, but I have disabled fastboot/hibernation before starting the process.

Since my previous post, I have tried another thing: I have used Rufus to create an UEFI version of the USB install drive. However when booting on this new version, I get an error message telling me that I am booting in legacy mode on a UEFI drive. But I have checked at least five times the BIOS and it is clearly set to UEFI. I am really lost.

I will run boot repair and see what comes out of it.

---

### Post by ludovictheate on 2019-04-25
Hi, 

Further to my previous reply, I have run boot-repair : the URL is [http://paste.ubuntu.com/p/jCHCVcWt5h/](http://paste.ubuntu.com/p/jCHCVcWt5h/)

---

### Post by dino99 on 2019-04-25
As i understand, your problem is with the bootloader (grub2) not used but the w10 one.
Where have you set the grub2 installation ?

 [https://ubuntuforums.org/showthread.php?t=2276498&page=5](https://ubuntuforums.org/showthread.php?t=2276498&page=5) (better read the most recent posts, as grub2 have changed a bit with time)
[https://askubuntu.com/questions/1031993/how-to-install-ubuntu-18-04-alongside-windows-10](https://askubuntu.com/questions/1031993/how-to-install-ubuntu-18-04-alongside-windows-10)

---

### Post by oldfred on 2019-04-25
Boot-Repair says you are booting in Legacy/BIOS/CSM boot mode.
The setting in UEFI for UEFI or BIOS/legacy is for your actual installs.
You can normally boot USB in either mode separate from UEFI default settings.
UEFI boot menu should offer both "UEFI:flash" or "flash" which is then BIOS mode. Flash will be name or label of flash drive. One of my systems just calls it pmap. And that system will only boot in UEFI mode if settings are "UEFI only". The setting for 'UEFI or BIOS' only booted in BIOS mode.

You have UEFI system and UEFI install of Windows on sda.
But have also installed various BIOS boot loaders to the gpt drive's protective MBR. Never boot in BIOS mode as it will start to boot & fail. Those boot loaders just never should be used. But often more dangerous to erase than just leave them.

See also link below on install steps for even more info.

---

