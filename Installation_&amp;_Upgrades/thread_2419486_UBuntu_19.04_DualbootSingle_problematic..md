---
title: "UBuntu 19.04 Dualboot/Single problematic."
date: 2019-05-22
forum: Installation &amp; Upgrades
---

### Post by mkamran94 on 2019-05-22
Installing this on a Thinkpad X1 Extreme

With an i7, GTX 1050 TI MAX-Q., 1 TB SSD, 16 GB RAM.

Came with windows 10 shrunk SSD by 200 GB for Ubuntu installed Ubuntu on it but first...

1 --> Installer froze on connecting with WiFi on installation so then I restarted and avoided wifi installer proceeded without issues. On finish as I tapped restart laptop froze forced a restart no luck with boot.

2 --> Deleted everything for a single Ubuntu install avoided WiFi again and AGAIN on restart it froze forced a shut down on start it froze on login...

This Thinkpad is more of a s**t show then I thought.


--- Figured it out, it's the GTX 1050 Ti I'll use Intel for now until I can install it the drivers somehow.

---

### Post by oldfred on 2019-05-22
Some do install with Intel and then add nVidia drivers.
Normally you need nomodeset boot parameter to install & initial boot or until you install nVidia driver from Ubuntu repository. 

At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) & 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

# make sure system is up to date
sudo apt-get update
sudo apt-get upgrade

sudo apt-add-repository ppa:graphics-drivers/ppa
sudo apt-get update

# If later you do not want ppa, how to uninstall ppa
sudo add-apt-repository --remove ppa:graphics-drivers/ppa

# should show newest versions available in addition
ubuntu-drivers devices
You then can manually choose any in list.
sudo apt-get install nvidia-XXX 

Details on driver ppa
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)

Installing GNU/Linux on a 2014 Lenovo Thinkpad X1 Carbon UEFI/BIOS suspend to RAM issue
[http://mako.cc/copyrighteous/installing-gnulinux-on-an-2014-lenovo-thinkpad-x1-carbon](http://mako.cc/copyrighteous/installing-gnulinux-on-an-2014-lenovo-thinkpad-x1-carbon)

---

