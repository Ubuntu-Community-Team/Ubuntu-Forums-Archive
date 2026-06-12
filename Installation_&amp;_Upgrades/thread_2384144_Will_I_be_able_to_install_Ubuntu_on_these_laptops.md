---
title: "Will I be able to install Ubuntu on these laptops?"
date: 2018-02-02
forum: Installation &amp; Upgrades
---

### Post by jspan on 2018-02-02
Hi,
I don't have a lot of experience with installing Ubuntu so I would like to make sure before I buy a new laptop. I am considering these computers and did not see them in the Ubuntu certified list (at least with the processor I want). 

I would be thankful if someone could consult me before I purchase a laptop. Will I be able to install Ubuntu in parallel to Windows 10? I am considering these two models:

1. Dell Inspiron 13 7000 2-in-1 i7-8550U 
     [http://www.dell.com/en-us/shop/dell-laptops/inspiron-13-7000-2-in-1/spd/inspiron-13-7373-2-in-1-laptop/dncwkb003h](http://www.dell.com/en-us/shop/dell-laptops/inspiron-13-7000-2-in-1/spd/inspiron-13-7373-2-in-1-laptop/dncwkb003h)
2. Dell Inspiron 13 5000 2-in-1 i7-8550U
     [http://www.dell.com/en-us/shop/dell-laptops/inspiron-13-5000-2-in-1/spd/inspiron-13-5379-2-in-1-laptop/dncwsar5012bh](http://www.dell.com/en-us/shop/dell-laptops/inspiron-13-5000-2-in-1/spd/inspiron-13-5379-2-in-1-laptop/dncwsar5012bh)

I also considered the Lenovo Yoga 720 but read that there are some issues.

Thank you very much,
Jeremy.

---

### Post by oldfred on 2018-02-02
Very new hardware may need newest Ubuntu version with newest kernel and newer video drivers.

 Dell XPS 13 9360 16.04 worked after nvme firmware & BIOS update, 16.10 did not, new rEFInd for NVMe
[http://askubuntu.com/questions/884991/ubuntu-16-10-dual-boot-error-grub-efi-amd64-signed-package-failed-to-install](http://askubuntu.com/questions/884991/ubuntu-16-10-dual-boot-error-grub-efi-amd64-signed-package-failed-to-install)
Dell XPS 13 9360 Dualboot Windows 10 and Ubuntu 16.04 AHCI NVMe
[http://askubuntu.com/questions/867488/dell-xps-13-9360-dualboot-windows-10-and-ubuntu-16-04?noredirect=1#comment1344306_867488](http://askubuntu.com/questions/867488/dell-xps-13-9360-dualboot-windows-10-and-ubuntu-16-04?noredirect=1#comment1344306_867488)
Ubuntu 16 on the DELL XPS15 9550 Tutorial
[https://ubuntuforums.org/showthread.php?t=2345444](https://ubuntuforums.org/showthread.php?t=2345444) 

 Dell UEFI Dual boot instructions using Something Else
[https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN](https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN)
[https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en](https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en)
Dell with NVMe needs AHCI & boot option nvme_load=YES
[https://www.dell.com/support/article/us/en/19/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en](https://www.dell.com/support/article/us/en/19/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en)
Dell XPS 13 9360 
[https://ubuntuforums.org/showthread.php?t=2353288](https://ubuntuforums.org/showthread.php?t=2353288)
Dell XPS 13 9560 install without issues
[https://ubuntuforums.org/showthread.php?t=2357321](https://ubuntuforums.org/showthread.php?t=2357321)
[https://wiki.archlinux.org/index.php/Dell_XPS_15_9560](https://wiki.archlinux.org/index.php/Dell_XPS_15_9560)

---

### Post by jspan on 2018-02-03
Thank you for the answer. These are different models. Should I understand by this that if the newest version of Ubuntu works for XPS than it should work for the new Inspiron?

---

### Post by oldfred on 2018-02-03
Dell has been pretty consistent with working well with Ubuntu.
It even offers models with pre-installed  Ubuntu, so most hardware works.
But even then sometimes drivers or kernels need to be the very newest version to include all the features needed with very new hardware.

A now year old thread, so older model. but some of the issues a user may have to work thru with new hardware.
[https://ubuntuforums.org/showthread.php?t=2342359](https://ubuntuforums.org/showthread.php?t=2342359)

---

### Post by TechnoJunky on 2018-03-06
I don't believe Dell supports Ubuntu on any laptop, only desktops.  I just purchased a Dell Inspiron 15 5000, with Nvidia 1050.  With the exception of a minor issue during the install process, Kubuntu 17.10 installed and has been working flawlessly.  I've been using it for about a week now.

---

### Post by mastablasta on 2018-03-07
> **TechnoJunky said:**
> I don't believe Dell supports Ubuntu on any laptop, only desktops. 

your belief is flawed: 
[http://www.dell.com/learn/us/en/555/campaigns/xps-linux-laptop_us](http://www.dell.com/learn/us/en/555/campaigns/xps-linux-laptop_us)

[https://www.omgubuntu.co.uk/2017/11/new-dell-precision-laptops-ubuntu-preinstalled](https://www.omgubuntu.co.uk/2017/11/new-dell-precision-laptops-ubuntu-preinstalled)

though they do hide them well. but in developing countries i've seen them prominently displayed. 

inspirons were usually compatible.

to the OP if the only difference between certified and the one you want is a different intel CPU, then it will work. intel CPu have kernel opensource driver support. intel makes drivers for linux.

---

