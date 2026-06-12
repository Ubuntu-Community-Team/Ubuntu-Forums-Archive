---
title: "problems with installation"
date: 2011-11-08
forum: Installation &amp; Upgrades
---

### Post by zakrs on 2011-11-08
Hi, I never thought that I’ll write here since I already successfully installed ubuntu on 3 of my friends computers but I cannot install it on mine. The live CD (original, purchased) will not work either. Same goes for xubuntu and kubuntu (working perfectly well on my friends computers)…It gives me all sorts of errors, from killing ports, slow ata4 to black screen. Wubi will get to reboot but that is it. Shows dual boot, I click on normal start and…black screen. 
I have dual pentum 6400, 2 gb ram, nvidia gt9500, "slow" dvd (ata4) win7 and a number of devices connected to my computer including fax card, 2 professional printers (brother and hp) and a web cam.
I probably got too hooked on it and don’t see the obvious…can you see what it can be?
Thank for your help.

---

### Post by oldfred on 2011-11-08
Welcome to the forums.

My desktop is a Dual core 6500 with nVidia 9600gt. I have had to use nomodeset on all boots until I get nVidia installed. I only install the nVidia that Ubuntu suggests as the current, but some newer versions have installed the older 173 driver which I uninstalled and then installed current.

Natty Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
I had to do this with my Nvidia 9600GT:
To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.
USB boot - At the menu press tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'. 
then
On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

---

### Post by zakrs on 2011-11-08
I think I&#8217;ve tried that and that&#8217;s was the point it came out with ata4 errors. But I&#8217;ll try that again following precisely your instructions or, it&#8217;s just a thought&#8230;I have as well ATI card. Do you thing if I swap it with nvidia, try to install ubuntu and after successful installation I swap the cards again (from ATI to nvidia) will it work?
Thank you for your answer.

---

### Post by oldfred on 2011-11-08
ATI & nVidia need different drivers. Switching will cause issues. 

Normally those who use a flash or USB drive have ways to revert to generic drivers that let them boot or a script to switch drivers before rebooting if using the USB on different systems with different video systems.

---

