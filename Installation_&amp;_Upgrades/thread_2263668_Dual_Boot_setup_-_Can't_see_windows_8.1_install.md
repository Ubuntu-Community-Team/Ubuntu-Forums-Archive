---
title: "Dual Boot setup - Can't see windows 8.1 install"
date: 2015-02-02
forum: Installation &amp; Upgrades
---

### Post by kl365 on 2015-02-02
[FONT=verdana]I've been trying for a few days to get a dual boot Windows 8 / Ubuntu setup running but nothing I seem to do will let me see the host OS when trying to install linux along windows 8.[/FONT]

[LIST=1]
[*]I have windows 8 installed on my HDD
[*]Disabled Fast Boot in the OS
[*]Followed directions to disable UEFI Secure Boot options.
[/LIST]
[FONT=verdana][http://imgur.com/wF36Oyw]("http://i.imgur.com/wF36Oyw.jpg") [1] - No detected OS[/FONT]
[FONT=verdana]I have a MSI Z77A-G43 motherboard so when I first entered the BIOS to check on the secure boot options I had to find the feature under the "Windows 8 Features" which was already set to disabled:[/FONT]
[FONT=verdana][http://imgur.com/T4RPrh7]("http://i.imgur.com/T4RPrh7.jpg") [2] - Fast Boot Disabled[/FONT]

[LIST]
[*]note that "Windows 8 Feature" is disabled.
[/LIST]
[FONT=verdana]I tried to run the install but was unable to detect the host OS again so I went back into BIOS to confirm that it was disabled:[/FONT]

[LIST]
[*]enabled windows 8 features - confirmed all fast boot options were off and confirmed secure boot is off -[http://imgur.com/57nG7LE]("http://i.imgur.com/57nG7LE.jpg") [3] - Secure Boot Disabled
[/LIST]
[FONT=verdana]At this point if I leave the "Windows 8 features" option set to Enabled even though all suboptions are disabled I receive the following error:[/FONT]

[LIST]
[*][http://imgur.com/TjKGmEW]("http://i.imgur.com/TjKGmEW.jpg") [4] - system bios detected non-windwos 8 logo graphic card. I have a GTX 650ti which has the windows 8 logo on the box and I've made sure I have all the latest drivers installed.
[/LIST]
[FONT=verdana]If the Windows 8 Feature are all disabled then the secure boot option should also be disabled and the OS should be visible correct? When I explicitly try to disable each sub-option I am unable to boot my computer because of a weird graphics card drive issue?[/FONT]
[FONT=verdana]Any suggestions?[/FONT]

---

### Post by oldfred on 2015-02-02
I have not seen a UEFI/BIOS complain about the graphic card.
 UEFI, Windows on SSD, Ubuntu on HD ASRock Z77 Pro4 motherboard
[http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/](http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/)


But newest Widows is not enabling TPM, do you have any settings for that?
 Some UEFI also have TPM 
[http://technet.microsoft.com/en-us/windows/dn168169.aspx](http://technet.microsoft.com/en-us/windows/dn168169.aspx)
UEFI secure boot doesn't have anything to do with a TPM.
[https://www.ibm.com/developerworks/community/blogs/smartersecurity/entry/uefi_secure_boot_and_the_tpm20?lang=en](https://www.ibm.com/developerworks/community/blogs/smartersecurity/entry/uefi_secure_boot_and_the_tpm20?lang=en)
Microsoft has announced that from January 1, 2015 all computers will have to be equipped with a TPM 2.0 module in order to pass Windows 8.1 hardware certification.
[https://en.wikipedia.org/wiki/Trusted_Platform_Module](https://en.wikipedia.org/wiki/Trusted_Platform_Module)
Re: certificate to verify signature of Ubuntu kernel 
[http://ubuntuforums.org/showthread.php?t=2259248](http://ubuntuforums.org/showthread.php?t=2259248)

And nVidia has drivers with some cards with some security that is not yet in the open source driver, so you have to have the nVidia driver. Best to install from Ubuntu repository unless a very new Maxwell card.

You also have fast boot settings in Windows as well as UEFI.
      
 Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
Fast boot is hidden.
If issues you may need these?
Control Panel -> Power icon -> Choose what power buttons do -> Change settings that are currently unavaliable, make sure fast startup is unchecked 
powercfg /h off

    
Do you have the latest verion update for UEFI from MSI?

 MSI UEFI bug work around A75MA-G55 UEFI boot entries disappear 
[http://forum-en.msi.com/index.php?topic=153411.0](http://forum-en.msi.com/index.php?topic=153411.0)
[http://forum-en.msi.com/](http://forum-en.msi.com/)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1129524](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1129524)

---

