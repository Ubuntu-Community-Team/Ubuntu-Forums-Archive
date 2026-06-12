---
title: "Dell Inspiron 17 Model 3721 - No option to boot from DVD in UEFI mode"
date: 2015-02-12
forum: Installation &amp; Upgrades
---

### Post by PopsTheSailor on 2015-02-12
My tripple boot setup is hosed. Need help. 

I have a Dell Inspiron 17 model 3721 with Windows 8 and 2 Ubuntu 14.04 Mate's installed. Grub 2 is not working. I can't boot into any of them. I've tried boot repair but is says I'm in Legacy mode and need to switch to UEFI mode. Here's the rub.

I've read several posts that says you have to disable secure boot in  order to boot from a DVD in UEFI. I have done that and there is still no  option to boot from a DVD. The only way I boot from a DVD is through Legacy  mode but I need to boot from a DVD under UEFI. 

When I try to go into Legacy mode so I can run Boot-Repair off the DVD boot repair says I need to be in UEFI mode. There is no DVD option in UEFI. Catch 22 - thanks Heller!

So, more research. Ah, you have to add your DVD manually, well, I have also tried that using these steps:

  1. Boot into setup
 2. Go to boot menu

 3. Click on Add Boot Option

 4. Enter a name such as DVD Drive

 5. Highlight DVD Drive Option and press enter

 6. Only 2 options appear to assign a file system to the boot option manually that I manually created.  Both are HDD partitions. No DVD drive appears in the list. 

Anyone have any ideas?

---

### Post by PopsTheSailor on 2015-02-12
Sorry, me again:

To understand what is happening, when I boot the laptop I get a black screen that says the following:
******************************************
GNU Grub version 2.02~beta2-15

Minimal BASH-like line editing is supported. For the first work. TAB lists posible command completions. Anywhere else TAB lists possible device or file completions.

grub>

---

### Post by oldfred on 2015-02-12
Is that from a BIOS/CSM boot or from a UEFI boot?

Some UEFI require you to allow UEFI boot with secure boot off. That is another separate setting or even some systems require a password to open more settings.

But I thought Dell's worked. But most use flash drive now as it is reusable and faster.

       Dell XPS13 - New Broadwell, not yet fully supported Feb 2015
[http://major.io/2015/02/03/linux-support-dell-xps-13-9343-2015-model/](http://major.io/2015/02/03/linux-support-dell-xps-13-9343-2015-model/)
[http://askubuntu.com/questions/395743/how-to-install-ubuntu-on-xps-15-platinum-2014-version-properly](http://askubuntu.com/questions/395743/how-to-install-ubuntu-on-xps-15-platinum-2014-version-properly)
Dell XPS 8700 with Intel SRT -  Install 13.10 - just change UEFI to AHCI mode
[http://ubuntuforums.org/showthread.php?t=2199382](http://ubuntuforums.org/showthread.php?t=2199382)
Dell Inspiron 3521
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)
Ubuntu on the Precision M3800 or XPS15 Nov 2013
[http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)
[https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z](https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z)
Dell 14z & 17r with Intel SRT
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)

---

### Post by PopsTheSailor on 2015-02-12
It's from a UEFI boot I believe. The grub message above shows up on both Ubuntu installs I have. Oddly enough, if I select Windows (ver 8 if it matters) it boots into windows just fine.

I don't have a usb stick available right now and although that would most undoubtedly work, the bigger issue is that I can't get an option to boot in UEFI on a DVD.

Secure boot is off. I looked at every option in setup and nothing stands out. I'll have to try and dig up a flash drive I guess.

---

### Post by PopsTheSailor on 2015-02-12
OK, I've found a usb drive. How do I write the ISO to is? If I right click and select write to disk, the USB is not an option.

---

### Post by PopsTheSailor on 2015-02-12
Found the directions on how to install to USB. I used Unetbootin. DVD still an issue but boot repait has run and fixed my issues.

---

