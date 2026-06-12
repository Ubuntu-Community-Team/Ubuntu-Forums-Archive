---
title: "OS Upgrade from 14.04LTS to 15.10 and problems"
date: 2016-02-24
forum: Installation &amp; Upgrades
---

### Post by NotWindows on 2016-02-24
I upgraded the Ubuntu OS from 14.04lts to 15.10 and after a long time of the install the screen went blank. I left it alone for a while but nothing changed. I rebooted the computer but now have no dual boot and will not boot into Ubuntu, it seems to go into terminal and asks for login and password.

What do I need to do?

Help!

Thanks,
Kevin

---

### Post by oldfred on 2016-02-24
UEFI or BIOS system?
Then are operating systems installed in UEFI or BIOS?
Did you remove ppas and any proprietary drivers before upgrading? Often drivers or ppas prevent full update. 

If you get grub menu, you may need to reinstall proprietary drivers, most often video.
What video card/chip?

May be best to see details, from live installer, best to use 15.10 if that is what you have installed.
 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by NotWindows on 2016-02-24
Bios (I think) older computer
Did not remove any drivers
Video card is a Asus Nvidia GT430

Would it be easier to just do a fresh install of 15.10? I'm not really losing much of anything, already backed up the drive for my files.

---

### Post by oldfred on 2016-02-24
Sometimes new install is the easiest solution, if you have good backups and/or separate /home and exported list of installed apps to make it easy to reinstall all the apps you added.

But if nVidia have you tried nomodeset and then reinstall nVidia driver from repository.
Or you may be able to install nVidia driver from command line if you boot that far.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[URL="http://ubuntuforums.org/showthread.php?t=1613132"]http://ubuntuforums.org/showthread.php?t=1613132

[/URL]
 # list drivers available, same list as system settings,  software updates,  additional drivers or last tab
ubuntu-drivers devices
# or
ubuntu-drivers devices | grep recommended 

   sudo apt-get remove --purge nvidia-*
sudo ubuntu-drivers devices
sudo ubuntu-drivers autoinstall

[URL="http://ubuntuforums.org/showthread.php?t=1613132"]
[/URL]

---

