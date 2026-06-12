---
title: "Constant Kernel Panics while installing"
date: 2011-10-06
forum: Installation &amp; Upgrades
---

### Post by htt-thalan on 2011-10-06
People, I having something really weird going on here... I've been trying all fudging day and if I had any hair, i'd have pulled it out by now.
 
Here is the case:
 
I have a 9 month old Toshiba laptop here, a Satellite C660-108 model with an Intel Core i3 CPU, 2x1gb memory (DDR10600 and DDR8500), Intel onboard graphics, Realtek 8188CE wireless and a Toshiba 320gb 5400rpm disk.
 
It came with Windows 7 provided by Toshiba which I deleted because I use it primarily as a Linux try-out station for new distro's and projects.
 
It came to be that I tried my hand at Debian a few days ago, but I couldn't make it work so I wanted to install (K)Ubuntu again for normal use. And that's where the excrement hit the rotating metal blades. 
 
 
I have tried to install a wide selection of OS'es, being:
 
Ubuntu 11.04 64bit 
Kubuntu 11.04 64bit ánd 32bit
Kubuntu 10.04 LTS 32bit
Kubuntu 11.04 Alternate Install 64bit
Suse 11.4 KDE 64bit
Suse 11.4 Gnome 64bit ánd 32bit
 
To create the bootable memorystick to this end, I've used Unetbootin and Universal USB installer, both from my Toshiba Qosmio laptop, running Windows 7 x64. I've done this many times before, never had any problems before.
 
 
The case: During a GUI install of (K)Ubuntu the installer will crash during the 'copying files' bit, with as a common denominator always the following piece of error code:
 
"Kernel Panic - Not Syncing: Fatal Exception in Interrupt"
 
accompanied by the usual signs of a panic: Total Lockup and blinking caps lock (this laptop has no scroll lock light).
 
 
What have I tried so far to troubleshoot:
 
- switch hard drives (I had an identical Toshiba drive lying around from my Qosmio, only 500gb instead of 320gb)
- use only one of the 2 installed memory modules
- use only one memory module and try both sockets
- run memtest for multiple passes (never any errors)
- use different USB sticks
- switch disk support in bios from AHCI to compatible and back
- curse
- trying the install without network connection
- trying install w/ network connection, but w/o downloading updates during installation
- trying install without the '3rd party software' bit
 
I've had some strange results though. 
 
While doing a GUI install of 11.04 either with Ubuntu, Kubuntu and their respective 32bit and 64bit versions, I always get the aforementioned Kernel Panic.
 
When booting these OS'es from their respective Live environments, they seem to run just fine. The problem only arises when installing to the hard disk.
 
When installing 10.04 I get a working desktop environment, but 10.04 fails to support the wireless card in this specific laptop. I could try and get that working, but then I would work around the problem instead of solving it.
 
When *trying* to boot from a SUSE 11.4 usb stick, either 32bit or 64bit, I get a 'could not mount live image' failure, but it does this on other laptops too, with different usb sticks, so that might be a failure in creating the stick on my part.
 
 
Now, using the Kubuntu 11.04 alternate installer gets me a bit further, I managed to finish the copying fase up to the bit where it's supposed to install GRUB to the master boot record. I press 'yes' at which point it fails to install GRUB to SDA2.... which is an odd error for this laptop only has one HDD, meaning SDA2 must be the usb stick it's installing *from. *Ofcourse this could be due to the fact that it still regards the memstick SDA1 because the installer booted from it. I then chose LILO instead of GRUB and that went ok, only for the laptop to consistantly crash on boot when it arrives at the boot loader...
 
 
And now for the best part: I've been using this laptop for some time now, never had any problems with it: It has been running Ubuntu 11.04 for months without any problems... those only started after my experiment with Zentyal and Debian which proved unsuccesful, after which I thought I'd just slap 11.04 back on it and just experiment with the other two in a virtualbox.
 
Seems like this machine has been cursed! I'm at a loss here, anything else I should and could try to troubleshoot this? I might have forgot to mention some bits, it's late and I'm tired, but feel free to take shot.

---

### Post by dino99 on 2011-10-06
my installation way:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

about kernel panic, dont worry its quite common with some chipset/hardware. You need to boot with option: try first with either noacpi or nomodeset

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

you can also gloogle around: ubuntu+yourmodel+install

---

### Post by htt-thalan on 2011-10-06
Thanks for your rapid response, but I've tried numerous times to delete all existing partitions before installing something else (although the last time i tried that from an Ubuntu live environment I wasn't able to delete the existing swap anymore).
 
Also, I'm not trying to dualbooth anything, I'm doing a clean install.
 
Furthermore, this laptop has ran 11.04 without any problems (even during install) before, and lastly, the 'advanced options' menu section of these (K)ubuntu install sticks do not offer me the option of giving parameters during install, they just give me 'boot live', 'memtest', 'boot from first HD' or 'quit'.
 
About the googling: I havent been able to google anything useful about this. Suprisingly, I have been able to find a single hit on this subject since about 5 minutes ago, someone on the Ubuntu forums is have the exact same problem with the exact samen laptop, he even has the exact same username!
 
Yay for google indexing ;-)

---

### Post by htt-thalan on 2011-10-07
I just tried a cd with Ubuntu 11.04 x64 which I burned some time ago and never gave me any problems, but also this way of installing generates the same errors, so it's not the usb install either.
 
- edit -
 
Not knowing what else to try, I reinstalled the notebook with the originel Win7 x64 image that was supplied with it at purchase. Installation went without a hitch, OS works like a charm. 
 
What the fudge is going on here!
 
- edit 2 -
 
Via this fresly installed Windows 7, I downloaded a new Kubuntu 11.04 image, together with the required Universal USB installer, and created a new usb live stick. Booted that, tried to create a dualboot config with windows 7 instead of a 100% Kubuntu installation, same error, crashes at copying files.
 
The notebook is not broken, the software is not broken, but they refuse to work together now, even though they have done perfectly in the past.
 
I'm lost here.

---

