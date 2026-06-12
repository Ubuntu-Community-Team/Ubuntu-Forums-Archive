---
title: "netinstall using usb - GRUB problem."
date: 2008-05-03
forum: Installation &amp; Upgrades
---

### Post by suhewabe on 2008-05-03
I have a server with no cd rom, so I am using a USB flash drive to use the net installer to install 8.04 onto the hard drive.  I used the boot.img.gz technique to set up the USB drive and I am able to go through the installation setup.

After the setup is complete and it tells me to reboot the machine, I reboot and take out the USB drive.  When I do that it is unable to boot from the hard drive.  

I only set up 2 partitions on the HDD - one for / and one for swap, and I set the / partition with the boot flag on.

If I put the USB drive back in and reboot, it looks like the installer put GRUB on the USB drive because I get the GRUB prompt this time around, and not the install setup.

Any advice on how to make the HDD boot up ubuntu would be fantastic.

---

### Post by Pumalite on 2008-05-03
Your Grub is probably half in the USB and half in the Internal. Do it again and this time make sure you install to sda. Your Flash must be sdd, but make sure with sudo fdisk -l
[http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html)

---

### Post by suhewabe on 2008-05-03
Thanks - I'm getting closer! 

I was able to install LILO onto the MBR of the hard drive from the install menus'.  Apparently it doesn't do it automatically and before you tell it to reboot to finish the install you need to go back to the menu and there's an option to install LILO or GRUB.

I don't know which one is better or more popular, so I chose LILO.  My problem now is that the HDD was labeled /dev/sdb during the installation, and now without the USB drive it's /dev/sda, so it's not booting correctly.

I think all I need to do is edit a file on the HDD, but I didn't see any edit apps in the command line that comes up after it can't start an OS.

Suggestions?

---

### Post by Pumalite on 2008-05-03
Super Grub can fix your Windows MBR. If you need to reinstall Grub>
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
[http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)

---

