---
title: "Installing ubuntu on a seperate Hard Drive?"
date: 2009-11-20
forum: Installation &amp; Upgrades
---

### Post by ojdon on 2009-11-20
Hey there, I've currently got Windows 7 (x64) installed on my SATA hard drive and I want to install Ubuntu on my IDE Hard Drive? How would I go about doing this since in the past I've installed Ubuntu on my IDE drive but got a "No such disk" error in GRUB.

---

### Post by oldfred on 2009-11-20
I have had issues with old grub and mixed Sata & Pata drives. New grub seems to be even worse and there is a bug where grub2 boots very slow if it installs in the MBR of one drive but the boot is in the other drive.

A normal install to the Pata may see the Sata as first and overwrite the MBR of the windows drive. Normally that is not a issue.

I like the idea of an operating system on every drive and in the MBR of that drive have the boot for that operating system. Of course only the first drive as defined by the BIOS will boot and windows will not boot ubuntu (without lots of help), so grub and ubuntu should be on the first boot drive. Ubuntu can map windows so it thinks it is the first drive and if you ever want to switch the order in BIOS the windows drive will still boot.

The safest way is to unplug the windows drive and install Ubuntu, then we have to go back and add the windows entry to grub after you plug the drive back in. In legacy grub you had to manually add the entry with grub2 you can run an update-grub command and it should find windows and add it to grub.cfg.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
[http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm](http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm)
[http://members.iinet.net/~herman546/](http://members.iinet.net/~herman546/)
[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

---

