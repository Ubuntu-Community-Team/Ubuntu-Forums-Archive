---
title: "Direct Boot from BIOS BBS key?"
date: 2011-07-03
forum: Installation &amp; Upgrades
---

### Post by Coastalguy on 2011-07-03
I currently have Ubuntu Meerkat and 2 XP's installed on 2 drives. On bootup, it first goes to Grub, where there is a Windows selection that goes to the Windows boot loader where I can select the XP that I want to load.

I now want to replace one of the XP's, that I use as a backup, with Windows 7 to test it for any software or hardware problems, before making it a Windows working OS, as I currently have with my main XP. I also want to continue working on Ubuntu for testing and also a backup working OS.

I understand that you cannot just install Windows 7 in place of one of the XP's, and have it replace the boot line on boot.ini, as Win7 now uses it's own Boot Manager replacing boot.ini. I also understand that Ubuntu can mess up the Win7 installation.

It was suggested that I disconnect the drive with Ubuntu and then load Win7 with my working XP on my main drive so that it doesn't "see" the Ubuntu OS and consequently sets up the boot Manager for just my existing xp and win7. 

I am then told to reconnect the drive with Ubuntu and boot it using the BIOS BBS key, interrupting the Windows boot, or otherwise boot Windows boot manager by not using the Bios key and letting the regular boot up continue. As the BIOS BBS key is a new thing to me, my explanation is based on what I have read, if correct....

First, can someone confirm that this would be the way to go, and second, since bootup now goes to Grub and then to Windows, how do I have bootup go directly to the new Windows Manager, getting grub out of the boot process?

This whole thing with Ubuntu and Win7, seems complex and confusing, so I am not sure how to accomplish all of this. Any suggestions?:(

---

### Post by oldfred on 2011-07-03
You can and should have different boot loaders on different drives. What is the issue with booting grub and then choosing windows?

The BIOS one time boot key or a full change in BIOS will let you choose which drive to boot. But grub2 will let you choose also where windows will not.

If you disconnect the Ubuntu drive, be sure to reinstall the windows drive as sda. Windows is less tolerant of drive number changes. Ubuntu/grub also uses drive number, but then searches on UUID to find bootable partition so different drive number usually work.

Windows boot loader only can boot one active (boot flag) partition. It literally moves the boot files from any other windows into the one with the boot flag. If you overwrite the install with the flag which is what it will do by default then you will not have the boot files for the second install. Windows may update it.
With some trickery you can make it so grub can boot either windows directly, but then windows will not have the option to boot the other windows.

To get each MS to have its own boot loader make a primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

---

### Post by Coastalguy on 2011-07-05
Oldfred,

I have no problem, booting to GRUB, selecting windows and then booting the appropriate windows. This is what I am currently doing with Ubuntu Meerkat to Windows boot.ini to select either of my XP's.  However, as I want to replace my backup XP with Win7, I understand that the install of Win7 will remove GRUB from the MBR, whereby I will boot directly to the new Win7 boot manager and thus losing the GRUB boot selection. 

Reading the links you provided, it advises to load XP, then Win7 (which will detect XP) and then Ubuntu (which will detect both windows), giving me the same setup I have now except Win7 will be included with XP on the Windows boot loader.

My problem is, that I already have Ubuntu and XP installed and just want to install Win7 over the other XP. By doing this, I lose my boot to GRUB, so I am not sure how to then boot Ubuntu. I was told I could use the BIOS BBS key, but that didn't work. Is there any way to boot Ubuntu, if not included in the MBR sequence? I would hate to have to reinstall Ubuntu, as I have made a ton of changes in order to use XAMPP with NTFS partitions, among other installs etc.

Unless, there is a way to use the Ubuntu install CD to just fix the MBR, once I have installed Win7?

---

### Post by oldfred on 2011-07-06
If the windows is on a different drive than Ubuntu and you change BIOS to boot the windows drive before the install, then windows will put its boot loader on the windows drive. Then in BIOS change to boot the Ubuntu drive and run this to find the new windows install. If you followed the links above it will find two windows, otherwise the normal windows installs combines the boot files into one partition and grub will boot that and then from windows you choose which to boot.

After any system change, run this in Ubuntu.
sudo update-grub

If it happens to overwrite grub2's boot loader:
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)
Grub2 info & full chroot version - see METHOD 3 - CHROOT:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 and later with grub2) by talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

