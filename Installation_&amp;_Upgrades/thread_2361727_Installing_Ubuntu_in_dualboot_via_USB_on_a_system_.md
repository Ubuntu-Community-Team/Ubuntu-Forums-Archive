---
title: "Installing Ubuntu in dualboot via USB on a system that only has a PCIe based m2 drive"
date: 2017-05-20
forum: Installation &amp; Upgrades
---

### Post by isalirezag on 2017-05-20
Hello,
I am a Linux newbie.
I was trying to install Ubuntu on my windows 10 in a dual boot way and try to use it, but even from starting I faced a problem.
I have a Dell precision laptop, it has just an SSD hard drive.
After providing the Ubuntu on a USB and going to the very first steps, when we have to choose where to install Ubuntu I face problems.
When booting to the Ubuntu 16.04  on my system that only has a PCIe based m2 drive, the Installer cannot locate a hard drive and show the following fig:

 [IMG]https://cloud.githubusercontent.com/assets/12434910/26273936/f87a90cc-3cf0-11e7-8e38-ee44dfa43f59.png[/IMG]

I dont know what to do.
I found this explanation ([Here]("http://www.dell.com/support/article/us/en/04/SLN299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=EN")), but, honestly, I dont understand what it is saying.I dont know how to change the kernel or etc.
I would appreciate it if anyone can help me.
Thanks in advance.

---

### Post by LastDino on 2017-05-20
Have you first tried to go into BIOS and change SATA setting to AHCI ?

---

### Post by gordintoronto on 2017-05-20
You will also need to use the tools in Windows to shrink the largest Windows partition, to make space for Ubuntu.

What version of Ubuntu are you trying? With the latest hardware, 17.04 64-bit is your best bet.

Google this: community ubuntu boot parameters. The community docs have a lot of information, but some of it is out of date.

---

### Post by oldfred on 2017-05-20
I believe LastDino has most important setting change you need to make in UEFI for all Dells.
       
Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 

    
Dell UEFI Dual boot instructions using Something Else
 [https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN](https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN)
Dell XPS 13 9360 
[https://ubuntuforums.org/showthread.php?t=2353288](https://ubuntuforums.org/showthread.php?t=2353288)
Dell XPS 13 9560 install without issues
[https://ubuntuforums.org/showthread.php?t=2357321](https://ubuntuforums.org/showthread.php?t=2357321)
Dell XPS 13 9360 16.04 worked after nvme firmware & BIOS update, 16.10 did not, new rEFInd for NVMe
[http://askubuntu.com/questions/884991/ubuntu-16-10-dual-boot-error-grub-efi-amd64-signed-package-failed-to-install](http://askubuntu.com/questions/884991/ubuntu-16-10-dual-boot-error-grub-efi-amd64-signed-package-failed-to-install)
Dell XPS 13 9360 Dualboot Windows 10 and Ubuntu 16.04 AHCI NVMe
[http://askubuntu.com/questions/867488/dell-xps-13-9360-dualboot-windows-10-and-ubuntu-16-04?noredirect=1#comment1344306_867488](http://askubuntu.com/questions/867488/dell-xps-13-9360-dualboot-windows-10-and-ubuntu-16-04?noredirect=1#comment1344306_867488)
Ubuntu 16 on the DELL XPS15 9550 Tutorial
[https://ubuntuforums.org/showthread.php?t=2345444](https://ubuntuforums.org/showthread.php?t=2345444)

---

### Post by isalirezag on 2017-05-27
Yeah I tried all these methods. None of them worked for me:(
I had to return the laptop and ask Dell to install Ubuntu on it, which is kinda stupid but I did not have any other choices since it was making me crazy.
FYI, I also realized Dell wireless is not really a good choice for Linux!!!

> **LastDino said:**
> Have you first tried to go into BIOS and change SATA setting to AHCI ?


Yeah but that did not help :(

> **gordintoronto said:**
> You will also need to use the tools in Windows to shrink the largest Windows partition, to make space for Ubuntu.

What version of Ubuntu are you trying? With the latest hardware, 17.04 64-bit is your best bet.

Google this: community ubuntu boot parameters. The community docs have a lot of information, but some of it is out of date.

I did that and shrinked the largest windows partitions. I am trying to instal 16.04 LTS 64 bit since it is more reliable

---

