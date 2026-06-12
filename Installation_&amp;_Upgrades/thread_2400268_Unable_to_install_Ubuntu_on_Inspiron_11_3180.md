---
title: "Unable to install Ubuntu on Inspiron 11 3180"
date: 2018-09-04
forum: Installation &amp; Upgrades
---

### Post by skummer101 on 2018-09-04
Greetings,

I have an Inspiron 11 3180 that I am unable to install Ubuntu on.  

During the install or simply booted on the USB the machine locks up.  The cursor moves and they CAPS key lights up; but the rest of the machine completely unresponsive.

When I first aquired this machine; I was able to install Ubuntu 1804 on it with some difficulties.  I was finally able to install it with the minimal option selected and not having it connected to the network nor any USB devices (on the 5th attempt, try again, try again until it worked).  I have not been able to duplicate my previous succss this time.

I have attempted the install using Ubuntu 1804 and 1604 as well as Ubuntu Mate 1804 and 1604; all freeze at some point during installation.  Mostly at the beginning stages, other times during actual install.

I was able to install Windows 10 Pro and update the BIOS; this has not solved the Ubuntu installation error.

I then installed Debian 9.5.0 and it works like a champ.

I have also tried installing it with AMD PowerNow! disabled and enabled, Virtualization disabled and enabled, USB Emulation disabled and enabled.
EDIT:  have also tried UEFI enabled and disabled.

Don't get me wrong; I am a big fan of Debian, but I like Ubuntu more and would like to use it on this machine.

Any help would be APPRECIATED!

---

### Post by maurice33 on 2018-09-11
Thank you for the reply. The only way I could install Ubuntu is using Legacy in BIOS. I used the "try before you install" option. This went well until it locked up after a few minutes of use. I'm thinking it might not lock up if I actually installed it but I didn't want to chance it. I am not sure how or if it would boot after the install using Legacy either so I didn't install it. 

Regards to using Debian, I think I'll pass on this. I'll make the assumption that you were probably just happy to get something to install after all the effort and time you put into the other Linux installs. I understand your frustration. 

Dell directs people to go to this link in order to find out if your computer (laptop) has Ubuntu Desktop certified hardware:
[https://certification.ubuntu.com/certification/desktop/](https://certification.ubuntu.com/certification/desktop/)

This is the Dell link for How to Install Ubuntu Linux on your Dell PC:
[https://www.dell.com/support/article/us/en/19/sln151664/how-to-install-ubuntu-linux-on-your-dell-pc?lang=en](https://www.dell.com/support/article/us/en/19/sln151664/how-to-install-ubuntu-linux-on-your-dell-pc?lang=en)

Let me know if you ever get Ubuntu installed on your laptop. I too have the same model. I also tried to install Ubuntu on my other Dell laptop and ran into similar problems. You probably know this but if you hold down the power button for about 5 seconds when it locks up, it will power off and you can go back into BIOS or whatever you want to do. Best of luck.

---

### Post by akisveg on 2018-12-16
It seems to be probaply two reasons for this. Either is the first, or the second.
**1)**  The firmware bug that you mention is a Graphic card bug. When  your dell  frezzes, it actualy works but your graphic card has stoped.
This is a typical error "GPU has fallen off the bus" of the linux kernel since Jan. 2018. There are two options to fix this.
a)  Try to install a release of the distro you want that is released   earlier than Jan. 2018. (eg Ubuntu 17.10) This should fix the problem.  Then update the  system to the latest release through the software  updater. (if its a  rolling distro, it should update to the latest  version). If the problem  persists after the update, boot the updated  system using an older kernel  through grub. When linux updates, it keeps  the erlier versions of the  kernel and you can boot using anyone of  them. Do that until this linux  kernel bug regarding to the grapfics  driver is fixed.

b) Try to bypass the graphic driver when the system boots from the cd/usb using NVRM tools but you must know what you're doing.


**2)**  The second most probable reason for your laptop to freeze  during  instalation is that you have an M.2 drive that the installer  doesn't  recognize and it sees no drives to the pc. Usualy the installer  is  searching for the drive to be a sata/raid drive type /dev/sda1,sda2  etc.  M.2 cards are asigned differntly, through PCI express slot and no  a  SATA controler. You have to change this. Dell provides the steps  below: [https://www.dell.com/support/article...drives?lang=en]("https://www.dell.com/support/article/gr/el/grbsdt1/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en")


Keep in mind that it could be something else that frezes your laptop.
I hope it worked for you.
Cheers.

---

### Post by skummer101 on 2019-01-04
Thanks akisveg!

I threw on Ubuntu 18.10 and the machine is running like a champ.

Hopefully the issue will be fixed before the 18.10 clock runs out.

THANKS!

---

