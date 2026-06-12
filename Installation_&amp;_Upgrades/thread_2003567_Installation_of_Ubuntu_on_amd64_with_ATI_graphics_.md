---
title: "Installation of Ubuntu on amd64 with ATI graphics card"
date: 2012-06-14
forum: Installation &amp; Upgrades
---

### Post by iqtedar on 2012-06-14
I'm trying to install Ubuntu 12.04 on amd64 hardware with an ATI Radeon Xpress 200 graphics card using the desktop/live cd. At the point where I can set kernel parameters, I've selected all the options individually to no avail. The only combination that works is to select all of them (except free software option) but this disables the usb peripherals (and maybe more besides) so it is not a solution. So to install, I had to find and attach an old ps2 keyboard (with much difficulty because I only have a usb mouse). The system is installed but it does not boot from the hard drive. The monitor displays the message "video mode not supported".

Now I'm trying to figure out the problem by first getting the bootable cd to work. Using the vga=ask parameter, selecting  resolutions lower than 1280x1024 do not work and selecting this particular resolution brings up the above message.  Using the nosplash parameter for verbose mode shows the computer gets stuck at the point  "ACPI: Core Revision 20110623". The cd itself is fine because I've successfully installed on a computer with an Intel i3 processor without having to add any boot parameters. Also, an earlier version of Ubuntu and another variant fared no better. Is Ubuntu incompatible with amd64 hardware or the ATI graphics card, or is the monitor to blame for which I would have to find the ideal resolution, and if so how?

---

### Post by dino99 on 2012-06-14
xpress200 is no more supported by actual xserver, so try with an older one from natty for example

[https://launchpad.net/ubuntu/+source/xorg](https://launchpad.net/ubuntu/+source/xorg)

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by iqtedar on 2012-06-14
Thanks Dino99 for responding quickly but I'm not sure about the solution you are proposing i.e. how to go about uninstalling xorg and installing an older version on an installed system I can't even access. As for the open source driver, I think that might be worth considering if there are any hitches once I can get the system up and running.

By trying to address the "Cannot display this video mode" again, I followed the instructions at [http://askubuntu.com/questions/112957/display-works-fine-in-livecd-but-not-in-full-installation](http://askubuntu.com/questions/112957/display-works-fine-in-livecd-but-not-in-full-installation) and it seems I have edged further because I can now get the grub menu to appear when booting from the hard drive. But I still end up with a blank screen with a blinking cursor like before. I wonder if attaching a different monitor might make a difference or if I should specify a different resolution?

---

### Post by iqtedar on 2012-06-16
So how can I install the open source driver for ATI Radeon and on a system that I can't even get access to? The information on the official Ubuntu site at [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) and [https://help.ubuntu.com/community/RadeonXpress](https://help.ubuntu.com/community/RadeonXpress) do not provide any installation instructions, only how to purge fglrx. I've installed Ubuntu on older computers so why can't I install Ubuntu on this model from 2005 (HP Pavilion SlimLine s7520n Turion 64 ML-34, ATI Radeon Xpress 200G series)? If there is no solution, should I then abandon this computer or abandon Ubuntu?

---

### Post by Alivallo on 2013-02-17
Hopefully not too much time has passed:   

I too have been struggling with this and gave up on Linux years ago due to endless Command line, make/building packages, Flash, flavor/repository incompat, Wireless drivers, and Video Driver issues. 
 
Recently I came back to it for a number of reasons and improvements.   

It seems not much has changed for ATI video in the past years.  

After spending hours and wasted weekends on this you may need to **Purchase a different Video Card**.  When you do; search for a list of known linux compatible video cards your system supports and stay away from any hardware that requires a workaround or proprietary drivers such as NDIS Wrappers; FGLRX, etc.    

In fact even in windows ATI Radeon cards of this build type give me nothing but issues.  I've probably installed more then 5 Nvidia cards and spent hours/days getting the drivers right only to return them over the years.  same thing with Linksys pci wireless cards.

---

