---
title: "Cannot start Lubuntu after installation - artifacts."
date: 2013-10-11
forum: Installation &amp; Upgrades
---

### Post by chaushev on 2013-10-11
Hey, everybody. Ive got an old PC that I want to install Lubuntu on. It runs on Windows XP and I intend to use a dual boot system. Here are the specs:
CPU: [Intel Celeron D 315, 2266 MHz (17 x 133)]("http://ark.intel.com/search.aspx?q=Intel%20Celeron%20D%20315")
GPU: [NVIDIA GeForce FX 5200 (128 MB)]("http://www.nvidia.com/page/products.html")
MB: [ASRock P4i45GL/GV/PE]("http://www.asrock.com/mb/index.asp?s=n")
Chipset: [[COLOR=#0000ff]Intel Brookdale-G i845GEV[/COLOR]]("http://www.intel.com/products/chipsets")
RAM: [COLOR=#0000ff]768MB
[/COLOR]Network:[Realtek RTL8139]("http://www.realtek.com.tw/products/productsView.aspx?Langid=1&PNid=7&PFid=10&Level=3&Conn=2")
Bios: [COLOR=#0000ff][FONT=verdana]P3.40
[/FONT][/COLOR][COLOR=#000000][FONT=verdana]I installed the 12.04 version using WUBI (it only supports 12.04 Lubuntu). Rebooting after installing and running Lubuntu for the first time I get this
[/FONT][/COLOR][[IMG]http://img837.imageshack.us/img837/9291/qowg.jpg[/IMG]]("http://imageshack.us/photo/my-images/837/qowg.jpg/")
[COLOR=#000000][FONT=verdana]Tried running 13.04 on a live CD...i get the same issue trying to boot the OS live so i didnt even bother installing it - it takes a lot of time and hanging as my CD-ROM is pretty old too.[/FONT][/COLOR]
I have tried the Verbose mode, Save mode and Normal mode all ending up like this. In one of the modes in which you could see stuff loading, the line that showed last was : 
**Stopping enable remaining boot-time encrypted block devices [OK]**


I am quite new to Linux so I got no idea what this means. Could you help me?
Thanks in advance!

---

### Post by TenPlus1 on 2013-10-13
It seems that the open-source Noveau drivers for your nvidia card are having problems displaying the screen and you may need to install Nvidia's own binary driver for it to work properly...  Problem is you cannot see the desktop to do this so while booting Lubuntu hold down SHIFT to enter Recovery Mode and when the menu appears enable networking and drop to a root prompt, from there type this command:  SUDO APT-GET INSTALL NVIDIA-173 which will install the older binary driver and hopefully fix your screen problems after a reboot...

---

### Post by chaushev on 2013-10-13
Actually, I am not sure if the OS itself is installed or not!
 I start WUBI in WinXP, it finishes and then asks for reboot. When i reboot I get two options > Windows XP and Lubuntu. After choosing Lubuntu I get "Finalizing isntallation..." and a 5 second countdown. If I press any button for additional options i get this screen:
[[IMG]http://img46.imageshack.us/img46/8459/uvfo.jpg[/IMG]]("http://imageshack.us/photo/my-images/46/uvfo.jpg/")
Does this let me choose the way I want to finish the installation? All of them gets me to the screen I mention in my first post. I only havent tried ACPI workaround because I dont know what it does. What should I do?

---

### Post by blom0344 on 2013-10-13
Hi , I am stuck at **exactly** the same point on an older WinXp laptop with 512 Mb RAM and a NVIDIA Geforce FxGo5350 graphics card.

NVIDIA has a driver for Linux that I downloaded (NVIDIA-Linux-x86-325-15.run), but no idea how to install this.


I got as far as using 'c' to get a command line  (from the screen with the 5 different options) which gives me a GRUP> to enter commands . The sh command cannot be uses as it is not recognized

---

### Post by ibjsb4 on 2013-10-13
> **chaushev said:**
> Nobody has any idea what these splash screen artifacts or whatever they are mean?

Did you install that driver package?

Another thing worth trying with older computers is nomodeset.

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by blom0344 on 2013-10-13
> 
Note that this option is sometimes needed for nVidia cards when using the default "nouveau" drivers. Installing proprietary nvidia drivers usually makes this option no longer necessary, so it may not be needed to make this option permanent, just for one boot until you installed the nvidia drivers.


This is from the referenced link.  However , no clue if given how to install those drivers.  Or , in other words how to install when the OS does not supply a desktop to work with

---

### Post by chaushev on 2013-10-13
> **ibjsb4 said:**
> Did you install that driver package?

Another thing worth trying with older computers is nomodeset.

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Thanks! Post #1 and #8 contain all the information needed for this problem. I selected Normal mode and pressed "e" to edit. Added **[COLOR=Red]*nomodeset*[/COLOR]**[COLOR=#000000][I] and It looked like this:
[/I][/COLOR]> [COLOR=#000000]*linux /ubuntu/install/boot/vmlinuz debian-installer/custom-installation=/ubuntu/install/custom-installation iso-scan/filename=/ubuntu/install/installation.iso automatic-ubiquity noprompt *[/COLOR][COLOR=Red]*nomodeset*[/COLOR][COLOR=#000000]* quiet splash boot=casper ro debian-installer/locale=*[/COLOR][I]en_US.UTF-8 console-setup/layoutcode=[I]us console-setup/variantcode= -- rootflags-syncio
initrd /ubuntu/install/boot/initrd.lz[/I][/I]Now the installation is running. After complition I guess I will have the same broken splash screen when I boot, as **nomodeset** works only for the current boot. All I will probably need to do after that is go into Recovery mode and install the Nvidia drivers using **sudo apt-get isntall nvidia-173**, just like TenPlus1 suggested in his post. That must do the trick. 

**Here is the explanation:**
> [COLOR=#000000]On some hardware configurations, you need to set some kernel parameters for ubuntu to boot or work properly. A common one is nomodeset, which is needed for some graphic cards that otherwise boot in to a black screen or corrupted splash, acpi_osi= to fix lcd backlight and other problems, and noapic and nolapic to work around various ACPI BIOS issues. In this how to I will explain briefly what this is and how to do it.[/COLOR]
> [COLOR=#000000]**nomodeset**[/COLOR]
[COLOR=#000000]The newest kernels have moved the video mode setting into the kernel. So all the programming of the hardware specific clock rates and registers on the video card happen in the kernel rather than in the X driver when the X server starts.. This makes it possible to have high resolution nice looking splash (boot) screens and flicker free transitions from boot splash to login screen. Unfortunately, on some cards this doesnt work properly and you end up with a [/COLOR]**black screen**[B]. Adding the nomodeset parameter instructs the kernel to not load video drivers and use BIOS modes instead until X is loaded. 

Note that this option is sometimes needed for nVidia cards when using the default "nouveau" drivers. Installing proprietary nvidia drivers usually makes this option no longer necessary, so it may not be needed to make this option permanent, just for one boot until you installed the nvidia drivers.[/B]
> WUBI: [COLOR=#000000](traditional way, if you downloaded the ISO or ran installed from a CD): after the windows part is completed you reboot to do the actual install (ubiquity is setup to auto-install to the defined virtual disk based on settings provided to wubi.exe in windows). [/COLOR][COLOR=#000000]
[/COLOR]> [COLOR=#000000]In the same way as the non-wubi install, [/COLOR]_the override is only in place for as long as the installation process_[COLOR=#000000]. After the unattended install the computer reboots, and the next time you select Ubuntu you get a normal looking grub menu (looks identical to normal installs at a high level) and [/COLOR]_you have to again apply the override as described in post #1_[COLOR=#000000]. After that, either install drivers, or override using permanently using /etc/default/grub.[/COLOR][COLOR=#000000]
[/COLOR]

---

### Post by mörgæs on 2013-10-13
Good, please mark the thread 'solved'.

---

### Post by chaushev on 2013-10-14
I am actually having another problem. I installed Lubuntu 12.04, the way I explained in my previous post. In order to boot with no problem I  have installed the nvidia 173 driver. At first I had no trouble, apart from the resolution which for some reason i could not set more then 800x600. I did an upgrade to 12.10 and then to 13.04 - I get blank screen trying to boot now. Any idea? I tried sudo apt-get update ...nothing to be updated. I got the nvidia 173 installed.

---

### Post by mörgæs on 2013-10-14
Have you tried a fresh install (no upgrades) of Lubuntu 13.10 using the approach you described above?

---

### Post by chaushev on 2013-10-15
I have made the **nomodeset** option permanent and now I boot normally. I get some strange black and white splash screens before the log in menu but nomodeset got the job done. What is bothering me now, is that I cannot change to resolution of the screen. The maximum allowed from the monitor settings gui is 640x480. I have tried some guides that suggested adding lines to some autostart menu but they didnt do the trick. All I need to fix for now is pretty much the resolution of the screen.

---

