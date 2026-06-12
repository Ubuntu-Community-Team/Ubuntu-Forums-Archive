---
title: "How to install a new .iso onto an SSD while in windows?"
date: 2020-01-15
forum: Installation &amp; Upgrades
---

### Post by PsychedelicWonders on 2020-01-15
So it's been a few years since I've messed with Ubuntu and I'm pretty rusty.

I have two OS SSDs, one for Windows 7 & one for Ubuntu.

I haven't used the Ubuntu SSD for a couple of years now and know it's outdated.

I also know that my boot loader is still messed up from the windows install, so I need help configuring that properly again as well.

But is there a way for me to just add the new Ubuntu .iso to the SSD while in Windows?

I don't have an extra thumb drive and if I can do it through windows since it's technically a separate SSD, that would be idea.

I also don't have a CD/DVD drive on this computer, so I can't burn a physical disc either.

Thanks!

---

### Post by CelticWarrior on 2020-01-15
No, you can't do it from Windows.

And Windows 7 is out of support so there's no point in keeping it around.

The best course of action is to invest in a cheap but reliable USB stick. 4GB is enough if you can find one; 8GB

---

### Post by PsychedelicWonders on 2020-01-15
Ok thanks.

Yeah that's why I'm adding an updated install of Ubuntu to my other SSD now that I'm unfortunately having to upgrade Win7 to Win10.

Whats the best way for me to get a report of my boot loader so I know what order my SSDs are currently loading in and if I have to change the boot loader once I update Ubuntu and also Win10?

---

### Post by oldfred on 2020-01-15
This can document your system.
Best to run from Ubuntu live installer.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

You also can run this from terminal. It actually is the first part of Boot-Repair and now has several forks.
Updated fork  as original bootinfoscript does not seem to be maintained
[https://github.com/arvidjaar/bootinfoscript](https://github.com/arvidjaar/bootinfoscript) 
[https://github.com/baedacool/bootinfoscript/blob/nvme-support/bootinfoscript](https://github.com/baedacool/bootinfoscript/blob/nvme-support/bootinfoscript)
Page with instructions and link to older download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by maryoung on 2020-01-16
> **CelticWarrior said:**
> No, you can't do it from Windows.

And Windows 7 is out of support so there's no point in keeping it around.

The best course of action is to invest in a cheap but reliable USB stick. 4GB is enough if you can find one; 8GB
At least 8 GB.

---

### Post by PsychedelicWonders on 2020-01-16
Ok what order should I do this so that I only have to do this once?

Should I upgrade to Win10 first

Then unplug that Windows SSD & plug the SSD in for Ubuntu and then run the new, updated Ubuntu .iso file

And then run this bootloader to fix Grub after both OS have been updated?

Would that be the best sequence?

Thank you!

---

### Post by P-I H on 2020-01-16
I did it in this order.
- Used an Ubuntu system to download Ubuntu and used mkusb to write the ubuntu iso to an USB stick
- Booted with the USB stick
- Used the method Erase disk and installed Ubuntu on sda. In this case ESP will be created on sda, which also will be used by Windows.
- Used the Windows installer to install W10 on sdb. This didn't work at the 1:st installation. I had to format sdb with a  GPT partition.

---

### Post by yancek on 2020-01-16
If windows is using UEFI it must be on a GPT disk.  This is not the case for Ubuntu or other Linux systems.  The best site to use for dual booting windows 10 uefi w/ubuntu is the official documentation at the site below. I guess you have it working but the site below would have probably saved some time and may be useful in the future.

---

### Post by ubfan1 on 2020-01-16
The Windows 7 install is almost certainly legacy, not UEFI, so if you run the Windows 10 upgrade, it will still be legacy.  For a fresh install of Windows, see if your machine supports UEFI, and use it (reformat disk using a gpt partitioning table). Having both Windows 10 and Ubuntu installed in the same mode is usually recommended (although in some machines which allow you to set a preference of boot mode) it really does not matter with separate disks for the OSes.

---

### Post by C.S.Cameron on 2020-01-16
If you download or make an image file, (.img), of an installed Ubuntu you want to use, it can be installed to SSD in Windows using Etcher "Dangerous" mode.
This is sort of like cloning a Ubuntu install.

Sudodus and I played with this for a while and it worked great, but the image files were large. He may have a recent .img file that can be downloaded.

See also: [https://www.howtogeek.com/228886/how-to-create-iso-files-from-discs-on-windows-mac-and-linux/](https://www.howtogeek.com/228886/how-to-create-iso-files-from-discs-on-windows-mac-and-linux/)

---

