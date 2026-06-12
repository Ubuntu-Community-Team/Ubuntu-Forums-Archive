---
title: "Monitor goes to sleep"
date: 2012-05-03
forum: Installation &amp; Upgrades
---

### Post by bamaredwingsfan on 2012-05-03
My problem is the exact opposite.  I can boot win7 64bit normally, but i can't get ubuntu to boot.  What happens is that my monitor goes into sleep mode before the ubuntu can finish booting.  I have an LG monitor, which i never had that problem before with my old PC which was an HP with win7 32bit.  But my new HP PC is win7 64bit, what gives?

---

### Post by oldfred on 2012-05-03
Welcome to the forums.

Your issue is not related to the thread you posted in so I moved it to its own.

What video card do you have. If nVidia I know nomodeset works. Is this from LiveCd/USB or after your install?

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
Press Ctrl and X to boot (low graphics mode), install nVidia driver suggested my Ubuntu

Natty or later Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

