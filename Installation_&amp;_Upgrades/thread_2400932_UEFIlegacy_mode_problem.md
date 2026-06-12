---
title: "UEFI/legacy mode problem"
date: 2018-09-11
forum: Installation &amp; Upgrades
---

### Post by alexchaos on 2018-09-11
Hello all, my first time here!

So I just started university and I have a Linux class that requires me to install Ubuntu.

I have both a laptop and a desktop and thought it would be a good idea to install Ubuntu on an external HDD so I can just plug it in either my laptop or desktop and have access to it.

I installed it and had no problem with my desktop. I set my boot sequence so USB has priority and when I plug it in my desktop it boots on Ubuntu otherwise it boots on Windows. No problem here. (MSI P65 GD55 motherboard)

Now here's my problem, when I plug it in my laptop (Lenovo Legion Y520) Ubuntu isn't detected. When I go into my BIOS there's no options to change boot sequence if it is set in UEFI. If I change it to Legacy mode, I can set boot order correctly BUT then windows is not detected anymore and gives me an error on boot that there's no OS detected. Only way too boot is to press F12 at start for boot menu and select external HDD for Ubuntu. Windows isn't in the list at this point.

Searched quite a lot on google and tried multiple things to no avail.

Any help is welcomed!

Thanks!

---

### Post by ubfan1 on 2018-09-11
It sounds like on the laptop you have Windows in UEFI mode, and on the external HDD,  Ubuntu in legacy mode.  Normally, the recommendation is to have both in the same mode, but my Lenovo W520 will boot both, you just select a preference when both are possible.  Use f12 to get the EFI menu, then select the device to boot -- Windows on sda should boot in UEFI mode, and Ubuntu on sdb(?) should boot in legacy.  Note, Ubuntu booting means running grub, which is then running in legacy mode, and certainly cannot at this point, boot Windows in UEFI mode.  Select any of the Ubuntu choices and they should run.

---

### Post by oldfred on 2018-09-11
Did you partition in advance and include an ESP - efi system partition on your external drive?
Everytime I install to a flash drive or external SSD, it overwrites my default Ubuntu UEFI boot on my internal drive. Or you do not have any boot files on external drive, just on internal drive.

My work around is to always partition in advance with an ESP as first partition. Then I have to copy all the /EFI/ubuntu folder twic to ESP on external drive. Second time to /EFI/Boot and then rename shimx64.efi to bootx64.efi.
That is because UEFI only boots external drives from /EFI/Boot/bootx64.efi. And you would have to select in UEFI boot menu each time.

With two different systems, you should not install any proprietary drivers as then it may not boot on other system. 

[https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator](https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator)

---

### Post by alexchaos on 2018-09-12
> **oldfred said:**
> Did you partition in advance and include an ESP - efi system partition on your external drive?
Everytime I install to a flash drive or external SSD, it overwrites my default Ubuntu UEFI boot on my internal drive. Or you do not have any boot files on external drive, just on internal drive.

My work around is to always partition in advance with an ESP as first partition. Then I have to copy all the /EFI/ubuntu folder twic to ESP on external drive. Second time to /EFI/Boot and then rename shimx64.efi to bootx64.efi.
That is because UEFI only boots external drives from /EFI/Boot/bootx64.efi. And you would have to select in UEFI boot menu each time.

With two different systems, you should not install any proprietary drivers as then it may not boot on other system. 

[https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator](https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator)


I think this is my problem, I just realized I don't have a partition with an ESP as first partition. I'll try this out when I come back home tonight! Thanks!

---

### Post by yancek on 2018-09-12
THe link below is the official Ubuntu documentation on dual booting with windows UEFI.  It gives a lot of detail and also explains the need to create a separate EFI partition.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

