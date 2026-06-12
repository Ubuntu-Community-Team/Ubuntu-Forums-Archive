---
title: "Used wubi, no root file system defined, so no Ubuntu"
date: 2016-03-15
forum: Installation &amp; Upgrades
---

### Post by ametheral on 2016-03-15
Used unetbootin to create a drive and booted my little Win7 PC off it, and was able to select "Ubuntu" from the list of operating systems. It started up what seemed to be normally, then gave me a message along the lines of "No root file system is defined". I can not use Ubuntu because of that error.

Issue #2: When I shut off the desired pc and reboot, the screen to select whether to use Windows or Ubuntu appears, and neither before nor after this screen can I access any boot settings screen. I can also not seem to uninstall the wubi install of Ubuntu.


[B]Essentially, all I need is the Windows 7 wiped, and ubuntu (12.04-15.04, don't care) permanently installed. 


What are my steps to correctly do so?[/B]

---

### Post by yancek on 2016-03-15
If this problem occurs during the install to hard drive from the flash drive it is because you did not set a mount point for the root of the filesystem which is the "/" symbol and is listed under the Mount point drop down window after you select a partition or unallocated space to edit.  This is shown on the page at the link below if you scroll just over half way down the page.

 [http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

If you used wubi, it is installed in your windows partition.  If you can boot windows, you can remove it by following the instructions at the link below, down near the bottom of the page.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

WUBI is no longer supported and has not been for several years and is recommended not to be used.

---

### Post by grahammechanical on 2016-03-15
> **(12.04-15.04, don't care)**

You should care. Ubuntu 12.04 reaches end of life April 2017. And 12.10, 13.04, 13.10, 14.10 & 15.04 have all reached end of life and are no longer supported.

So, it is either 12.04 with a little over 12 months support left; 14,04 with support until April 2019; 15.10 with support until July 2016 or 16.04 which is to be released at the end of April 2016 with 5 years support.

Regards

---

### Post by Frogs Hair on 2016-03-15
Hello and Welcome

Wubi is no longer supported and actually installs Ubuntu inside the Windows partition . If you want wipe Windows see the links. If you plan to wipe the drive get any files you want off of windows first. The graphical installer will guide you through the installation process. 

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by ametheral on 2016-03-15
> [COLOR=#000000]You should care.[/COLOR]

Can update to 15.04 once installed and I do thank you, however, for your valid reasoning.

---

### Post by ametheral on 2016-03-16
I uninstalled Ubuntu from Control Panel, though when I reboot it still lists both Windows and Ubuntu as available OS's. When I click on Ubuntu, it says there is an error with Windows and I take that to man the "loop" back to windows is broken. So I can not actually change boot settings, even with my fresh new USB mounted with the 15.04 ISO, because it only brings up this screen. What then?

---

### Post by yancek on 2016-03-16
If you removed the wubi install of Ubuntu, why click on the Ubuntu entry in the boot menu?  You deleted it.  If you want to remove the Ubuntu entry from the windows boot menu you need to edit the bcdedit file which is explained in the first paragraph in the Section how do I uninstall wubi at the wubi guide link I posted earlier.  According to the wuib guide, it uses the windows boot manager to boot.  Are you not able to boot windows?

---

### Post by ametheral on 2016-03-16
I can boot windows fine, I needed to know how to remove the Ubuntu entry and you have graciously answered that. I'll do that, then the original steps posted here and when done will mark as solved. Thank you yancek

---

### Post by ametheral on 2016-03-18
All done! Exactly how I wanted it to go.

Thank you grahammechanical, I installed 15.04 as recommended
Thanks to Frogs Hair for the 2nd link you provided
And to yancek for every post, notably the wubi uninstall guide and the bcdedit tip. The bcdedit was the key factor here.

Cheers,

Austin

---

### Post by oldos2er on 2016-03-18
> **ametheral said:**
> Thank you grahammechanical, I installed 15.04 as recommended

I don't see any such recommendation. Indeed, grahammechanical told you > ...15.04 have all reached end of life and are no longer supported. 15.10 is supported until July; 16.04 is an LTS and will be supported for five years.

---

### Post by Bucky Ball on 2016-03-18
> **oldos2er said:**
> I don't see any such recommendation. Indeed, grahammechanical told you  15.10 is supported until July; 16.04 is an LTS and will be supported for five years.

+1. Install 12.04, 14.04 or 15.10. The support has been explained. You are running an unsupported release. :|

---

