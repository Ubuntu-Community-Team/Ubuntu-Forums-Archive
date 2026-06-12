---
title: "Problems booting after fresh install"
date: 2014-09-08
forum: Installation &amp; Upgrades
---

### Post by Reese_Hackworth on 2014-09-08
Hi, so i've been trying to install Linux Variations on my Laptop computer.  Its an older HP DV9720.  I've tried Ubuntu, Linux Mint, and Zorin. Best i can tell from my research, the problem lies because for some reason my computer reads the hard drive as sdb and the USB install disk as sda.    I was able to get Elementary OS to install and boot, but it did read my hard drive as sda, but these other 3 variations seem to read it as sdb.  Once these three boot up, they go to the load screen then it drops me to an initramfs command line where its just a big circle of it not booting.  Any ideas what i can do make these Distro's see my disk drives as sda?  I've changed the boot order in the BIOS, tried removing the usb then booting, nothing seems to fix it.  Any ideas?

Thanks.

-RH

---

### Post by yancek on 2014-09-08
If you install any of them from a flash drive, you will have needed to set the flash to first boot priority in the BIOS.  When the installation is finished, you need to remove the flash drive and might need to change the boot priority back to the internal hard drive.

How 'old' is the computer?  Did you check the minimum hardware requirements before installing them?  Compare that to your hardware.
I've seen installs from a flash drive where the flash is shown as sda and the internal as sdb.  Other times the reverse.  Since a flash drive is generally consideerably smaller in size, it should be easy to determine which is which regardless of the label; sda/sdb.

So what is your situation now?  You have only Elementary installed and want to install some other system?

---

### Post by Reese_Hackworth on 2014-09-08
My system is aged, its dual core, bought it around 2009 or so, i've had older variants of linux installed on it before, which used to work years ago, i don't really understand why this isn't working, changing the boot order in BIOS seems to have no effect on the order the installer reads it.  I had elementary OS, but i've wiped it in favor of Zorin, its hard for me to say which Distro i really want, right now i just want one that will work lol, Elementary didn't let me have desktop icons, which was the main deal breaker for me, but at least it worked, even though it took forever to boot.  I have an SSD in this laptop as well.

---

### Post by nerdtron on 2014-09-08
Hmmm... so you get to install Ubuntu successfully? Have you tried installing using the "Something Else" option and reassign the partitions manually? You need at least two partitions, main partition "/", and swap partition. And also choose to install GRUB on the drive (like /dev/sda) on where you assigned the main / partition.

---

### Post by Reese_Hackworth on 2014-09-08
Yes, i have, but i haven't seen the option to install GRUB in the something else option.  It will say the install is successful, it will boot to the screen where i choose "Linux Distro", "Linux Distro Recovery Mode", or "Mem Test".  Choosing the distro starts it up, then i see the regular boot screen.  Then it drops to the [COLOR=#000000]initramfs command prompt.[/COLOR]

---

### Post by yancek on 2014-09-08
> Yes, i have, but i haven't seen the option to install GRUB in the something else option.

Using 'Something Else', the Installation Type window will have "Device for bootloader installation" below the main window and the default is /dev/sda.
If you can boot Zorin, do that and go to the site below and read the instructions from the link in the Description box on that page.  Download and run the script and post the output here, a results.txt script.

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

