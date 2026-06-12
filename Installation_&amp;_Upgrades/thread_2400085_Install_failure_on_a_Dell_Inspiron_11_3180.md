---
title: "Install failure on a Dell Inspiron 11 3180"
date: 2018-09-02
forum: Installation &amp; Upgrades
---

### Post by name0000 on 2018-09-02
This is a very low end laptop with a AMD A6 processor.

I've seen reports of other users installing Ubuntu on this machine but for me it doesn't work.
Even running a live image from a USB drive fails.

A few minutes after boot up the machine always hard locks up and the only recovery is to power off.
I have no idea how to even debug this.

Other Linux distributions work fine. I've tested Fedora and Manjaro, both install and work perfectly.

---

### Post by akisveg on 2018-12-16
It seems to be probaply two reasons for this. Either is the first, or the second.
**1)**  The firmware bug that you mention is a Graphic card bug. When your dell  frezzes, it actualy works but your graphic card has stoped.
This is a typical error "GPU has fallen off the bus" of the linux kernel since Jan. 2018. There are two options to fix this.
a)  Try to install a release of the distro you want that is released  earlier than Jan. 2018. (eg Ubuntu 17.10) This should fix the problem. Then update the  system to the latest release through the software updater. (if its a  rolling distro, it should update to the latest version). If the problem  persists after the update, boot the updated system using an older kernel  through grub. When linux updates, it keeps the erlier versions of the  kernel and you can boot using anyone of them. Do that until this linux  kernel bug regarding to the grapfics driver is fixed.

b) Try to bypass the graphic driver when the system boots from the cd/usb using NVRM tools but you must know what you're doing.


**2)**  The second most probable reason for your laptop to freeze during  instalation is that you have an M.2 drive that the installer doesn't  recognize and it sees no drives to the pc. Usualy the installer is  searching for the drive to be a sata/raid drive type /dev/sda1,sda2 etc.  M.2 cards are asigned differntly, through PCI express slot and no a  SATA controler. You have to change this. Dell provides the steps below: [https://www.dell.com/support/article/gr/el/grbsdt1/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en](https://www.dell.com/support/article/gr/el/grbsdt1/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en)


Keep in mind that it could be something else that frezes your laptop.
I hope it worked for you.
Cheers.

---

