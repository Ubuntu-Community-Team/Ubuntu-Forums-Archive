---
title: "Computer freezes at splashscreen on live cd's and USB"
date: 2012-08-28
forum: Installation &amp; Upgrades
---

### Post by Langney on 2012-08-28
Sorry to post this again 
 
Hi all I got a fairly new machine yesterday but the problem I am facing Is a weird one I've not come across before. Here goes. Currently I'm running Windows 7. So I go to the Ubuntu website to download the newest version. No problems there and burn't the cd at the slowest speed possible and ran test to see If the disk was all good. Here's where It gets complicated. I poped In the disk to ready for a restart. The computer restarts fine. I get passed the keyboard sign of the disk. Then the "Ubuntu" Splash sign with the dots going through and It crashes and stops. I have tried with various other distros too. I.E Beefy Miracle and the same happens again. Crash on splash so I kinda had enough and went to my local store to pick up the lastest version of Linux format as they are giving away 15 free distro's. Guess what? Same again :sad:

I really don't know what to do. Any advice would be super

My computers Specs are as followed 

Operating System
MS Windows 7 Ultimate 32-bit
CPU
Intel Core 2 Duo E6750 @ 2.66GHz 46 °C
Conroe 65nm Technology
RAM
4.00 GB Dual-Channel DDR2 @ 333MHz (5-5-5-1:cool:
Motherboard
Gigabyte Technology Co., Ltd. 965P-DS4 (Socket 775) 42 °C
Graphics
DELL E176FP (1280x1024@60Hz)
ATI Radeon HD 3800 Series (ATI) 52 °C
Hard Drives
140GB Western Digital WDC WD1500ADFD-00NLR1 ATA Device (SATA) 36 °C
Optical Drives
Optiarc DVD RW AD-5200A USB Device
Audio
AMD High Definition Audio Device


If nobody has a clue about this would be be possible to write Ubuntu onto the harddrive through another computer and transfer the Hard drive over?

Also an update. I tried with USB but the same result :(

Thank you very much

---

### Post by Karlchen on 2012-08-28
Hello, Langney.

Has your machine got a Broadcom WLAN adapter perhaps? There seems to be a whole bunch of Broadcom adaperts which will make Ubuntu 12.04 crash as long as the proprietary Broadcom driver has not been installed. (Which you cannot do when booting up live systems.)

Cf. the release note on "Boot hangs on systems using b43 wireless cards" **[here]("http://www.linuxmint.com/rel_maya.php")**. (Sorry, Mint release notes, but could not locate the corresponding warning in the **[Ubuntu 12.04(.1) release notes]("https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes")**.)
Cf. Launchpad bug report **[b43: missing firmware causes kernel panic]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/950295")**

Workaround:
Add the option "b43.blacklist=yes" to the Grub line loading vmlinuz as long as you have not added the proprietary driver.

HTH,
Karl

---

### Post by Langney on 2012-08-28
Hi Karl. I'm using the USB Netgear WNDA3100 wireless. Should I still try and add that line?

---

### Post by oldfred on 2012-08-28
Is this as you are starting to install or after installing.

It could be one of these three things. Video driver, other boot parameter or bug in Ubiquity.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
noapic nolapic noapci noirqpoll nosmp irqpoll
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)

Just saw this from arpanaut's post in another thread.
There is a bug in ubiquity on the 12.04 iso that causes the installer to crash part way through on some hardware.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/996568](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/996568)
From liveCD before install. 
sudo apt-get remove ubiquity-slideshow-ubuntu
or (ubiquity-slideshow-lubuntu) (and ubiquity-slideshow-xubuntu)
The Alternate iso is another option as it is text based and also does not use the slideshow.
[http://www.ubuntu.com/download/ubuntu/alternative-download](http://www.ubuntu.com/download/ubuntu/alternative-download)

---

### Post by Karlchen on 2012-08-28
> **Langney said:**
> I'm using the USB Netgear WNDA3100 wireless. Should I still try and add that line?
No. The workaround is for particular Broadcom devices only.
Rather follow the approach recommended by oldfred.

Karl

---

### Post by Langney on 2012-08-28
> **oldfred said:**
> Is this as you are starting to install or after installing.
 
It could be one of these three things. Video driver, other boot parameter or bug in Ubiquity.
 
How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
 
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
noapic nolapic noapci noirqpoll nosmp irqpoll
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)
 
Just saw this from arpanaut's post in another thread.
There is a bug in ubiquity on the 12.04 iso that causes the installer to crash part way through on some hardware.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/996568](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/996568)
From liveCD before install. 
sudo apt-get remove ubiquity-slideshow-ubuntu
or (ubiquity-slideshow-lubuntu) (and ubiquity-slideshow-xubuntu)
The Alternate iso is another option as it is text based and also does not use the slideshow.
[http://www.ubuntu.com/download/ubuntu/alternative-download](http://www.ubuntu.com/download/ubuntu/alternative-download)
 
 
Hello Fred. This Is at the begining. I've used Ubuntu on all my other computers and never come across this Issue. However, what I may try Is my old graphic's card to try and pinpoint what It Is. Could very well be my current card which Is a Radeon HD. All my other Ubuntu Rigs are Nvidia based.

---

### Post by oldfred on 2012-08-28
With nVidia I have had to use nomodeset on install and first boot. I think now you can install proprietary drivers as part of the update during install and it then installs nVidia immediately.

I had to do this with my Nvidia 9600GT:
To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.
USB boot - At the menu press tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'. 
then
On first boot after install, press e on getting the GRUB bootloader menu. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place

Some other settings, some have to force the Generic:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
* Older Intel video card: i915.modeset=1 or i915.modeset=0
* nVidia: nomodeset
* Generic: xforcevesa or nouveau.modeset=0
* Radeon: radeon.modeset=0

---

### Post by Langney on 2012-08-28
> **oldfred said:**
> With nVidia I have had to use nomodeset on install and first boot. I think now you can install proprietary drivers as part of the update during install and it then installs nVidia immediately.

I had to do this with my Nvidia 9600GT:
To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.
USB boot - At the menu press tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'. 
then
On first boot after install, press e on getting the GRUB bootloader menu. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place

Some other settings, some have to force the Generic:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
* Older Intel video card: i915.modeset=1 or i915.modeset=0
* nVidia: nomodeset
* Generic: xforcevesa or nouveau.modeset=0
* Radeon: radeon.modeset=0

Thank you Fred. I managed to get it to boot Into Ubuntu Live. Thats the first step complete :D Also thank you Karl :D

---

