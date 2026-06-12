---
title: "doing second ubuntu install to another partition from my current install"
date: 2011-04-27
forum: Installation &amp; Upgrades
---

### Post by bradmont on 2011-04-27
I want to set up a second install to play around with and have set up an extra partition for this purpose.  I would like to install 11.04 to the new partition from my current 10.10 install.  Essentially what I want to do is find a way to launch the installation system from an iso I've mounted as a loopback.

I want to do this from my current install so that I can continue using my computer while the installer is running -- I have other work to do at the same time (it will also save me burning a disc or overwriting a USB key).

A virtual machine is not an option because I want to use the new install to test out the performance of whole-disk encryption; virtualising the system would make this testing worthless.

(I am sufficiently experienced to deal with complex tasks, but I would rather avoid using debbootstrap et. al. if I can).

Thanks!

---

### Post by oldfred on 2011-04-27
I do not think you can do exactly what you want. You have to reboot even with a loopmount as far as I know. But if you do not check updates during install, you can install from a hard drive or USB very quickly. I installed 10.10 from USB loopmounted in about 10 Minutes, but updating took 15-20 (even with high speed connection) and configuring another 20+. In about an hour I system set up the way I wanted.

If you install, then upate, you can change your software source to an optimal source. System Administration, Update Manager, settings, Ubuntu Software tab, use combo box to choose other and let it find best local site to upgrade from.

ISO Booting with Grub 2 - drs305
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
HOWTO: Boot & Install Ubuntu ISO from the Grub Rescue Prompt
[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)
MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)

You can install grub2 and copy the ISO over without reformating a USB if you have room. The standard USB installers all reformat USB.
Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB")

---

