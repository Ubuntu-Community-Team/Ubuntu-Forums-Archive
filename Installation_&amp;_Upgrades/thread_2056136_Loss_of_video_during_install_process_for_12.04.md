---
title: "Loss of video during install process for 12.04"
date: 2012-09-10
forum: Installation &amp; Upgrades
---

### Post by robertj20112 on 2012-09-10
I am trying to install 12.4 LTS on my wife's Dell All-in-One Inspiron One.  I am using a previously-used CD image, so I know the CD is OK.  Install process starts normally with the line-by-line output, but before the graphical output starts, the display goes dark and stays dark.  Once the process reaches the point where a response is required to continue, it hangs there because there is no way to respond.  If I play with the mouse, I can sometimes get a quick flicker of the graphic image, but the screen then goes dark immediately.  I've installed every Ubuntu release since 8.4 on a number of different computers, but I have never experienced this problem!  Have tried a number of searches on the forums, but haven't hit upon any key which gets close to this problem.  Any and all help will be welcomed.  If I can't overcome this, my wife will be yoked to Windows 7....forever?
Please help if you can.  Thanks in advance.

64-bit Intel processor, 4 GB memory, I think an nVidia graphics card. (CORRECTION: Not an nVidia graphics card.)

---

### Post by oldfred on 2012-09-10
With nVidia, I always have had to use nomodeset.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Some have had this issue:
Just saw this from arpanaut's post in another thread.
There is a bug in ubiquity on the 12.04 iso that causes the installer to crash part way through on some hardware.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/996568](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/996568)
From liveCD before install. 
sudo apt-get remove ubiquity-slideshow-ubuntu
or (ubiquity-slideshow-lubuntu) (and ubiquity-slideshow-xubuntu)
The Alternate iso is another option as it is text based and also does not use the slideshow.
[http://www.ubuntu.com/download/ubuntu/alternative-download](http://www.ubuntu.com/download/ubuntu/alternative-download)

I had to do this with my Nvidia 9600GT:
To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.
USB boot - At the menu press tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'. 
then
On first boot after install, press e on getting the GRUB bootloader menu. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode), install nVidia driver suggested my Ubuntu

---

### Post by robertj20112 on 2012-09-11
> **oldfred said:**
> With nVidia, I always have had to use nomodeset.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Some have had this issue:
Just saw this from arpanaut's post in another thread.
There is a bug in ubiquity on the 12.04 iso that causes the installer to crash part way through on some hardware.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/996568](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/996568)
From liveCD before install. 
sudo apt-get remove ubiquity-slideshow-ubuntu
or (ubiquity-slideshow-lubuntu) (and ubiquity-slideshow-xubuntu)
The Alternate iso is another option as it is text based and also does not use the slideshow.
[http://www.ubuntu.com/download/ubuntu/alternative-download](http://www.ubuntu.com/download/ubuntu/alternative-download)

I had to do this with my Nvidia 9600GT:
To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.
USB boot - At the menu press tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'. 
then
On first boot after install, press e on getting the GRUB bootloader menu. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode), install nVidia driver suggested my Ubuntu

Thanks for the quick reply.  I'll try these suggestions as soon as I can persuade my wife to give up her computer for a few hours.

---

### Post by robertj20112 on 2012-09-11
Thanks, oldfred, your tip about "nomodeset" did the trick!  Now that PP is up and running, I've found another serious problem: the OS does not recognize the monitor and only offers 4:3 and 5:4 ratios for what is a 16:9 monitor.  Wife hates the stretched image!  Can I pursue this here, or should I start another thread?  Thanks, again, for solving the original problem.

Monitor is Dell Inspiron One 2320 all-in-one; running "lspci | grep VGA" tells me the following about the graphics: "VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)."  I originally thought the controller was an nVidia, but I guess I was wrong!  TIA

---

### Post by oldfred on 2012-09-11
Is this one of the dual video systems? Then I think you may need bumbebee. But I have not used it.

Optimus
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)
Bumblebee:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
NVIDIA Confirms It's Working On Optimus Linux Support - Aug 31, 2012
[http://www.phoronix.com/scan.php?page=news_item&px=MTE3MzY](http://www.phoronix.com/scan.php?page=news_item&px=MTE3MzY)

---

### Post by robertj20112 on 2012-09-12
It appears the Intel integrated graphics controller is the only one in the configuration.  Neither Ubuntu nor Windows 7 indicate an additional adapter is present.  Also, the Additional Drivers package does not show the availability of any proprietary drivers.  Any thoughts?

---

### Post by oldfred on 2012-09-12
It might be a setting in BIOS to turn on one or the other video cards??

Is it this model? I thought Intel just worked.
Guide to Get the Best Performace from the GMA 500 
[http://ubuntuforums.org/showthread.php?t=1229345](http://ubuntuforums.org/showthread.php?t=1229345)
Intel GMA500 "Poulsbo" video hardware
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/)
Ubuntu 12.04 has been officially released and, with minor adjustments, the intel gma500 video card is working out of the box.

---

### Post by robertj20112 on 2012-09-12
> **oldfred said:**
> It might be a setting in BIOS to turn on one or the other video cards??

Is it this model? I thought Intel just worked.
Guide to Get the Best Performace from the GMA 500 
[http://ubuntuforums.org/showthread.php?t=1229345](http://ubuntuforums.org/showthread.php?t=1229345)
Intel GMA500 "Poulsbo" video hardware
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/)
Ubuntu 12.04 has been officially released and, with minor adjustments, the intel gma500 video card is working out of the box.

Checked the BIOS, it's really simple.  Not a mention of the graphics adapter or anything video.  The BIOS is A06, dated 12/22/11, the CPU is G630.  I, too, thought Intel just worked, but not so far in this all-in-one.  I'll check out the link you gave me, and I'll keep digging.  Since the original problem has been resolved, I'll mark this thread as solved.  Thanks.

---

