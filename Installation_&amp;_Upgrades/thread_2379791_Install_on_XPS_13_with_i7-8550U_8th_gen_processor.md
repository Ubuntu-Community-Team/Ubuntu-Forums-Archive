---
title: "Install on XPS 13 with i7-8550U 8th gen processor"
date: 2017-12-09
forum: Installation &amp; Upgrades
---

### Post by crayiii on 2017-12-09
I just ordered a Dell XPS 13 9360 with the latest 8th gen Kaby Lake i7-8550U processor.  Since you can't order this configuration with Ubuntu I had to order it with Windows.  It has 16gb, 1TB, and the QHD touch panel.  I plan to remove Windows and install 17.10 but I can't find anything online about people's experiences installing on this laptop.  Does anyone here have experience with it?  Anything I need to watch for?

---

### Post by pointy2 on 2017-12-09
The Dell I've installed to is he 5378 13 7th gen i7 KabyLake architecture with intel dual band wireless 3165. While I have had problems with AA 17.10, I am believing that the install was due to user error (I'm a noob, ok?). As the architecture goes, your machine looks as if it can handle AA well...keep in mind, Dell packages Ubuntu in many of their pc's/lappys. 
The first thing you'll need is an AA liveUSB for the install, after, of course, you determine that your XPS is compatible per this site:
 
          [https://certification.ubuntu.com/certification/make/Dell/](https://certification.ubuntu.com/certification/make/Dell/)

You can get the AA torrent from here:

        [  http://releases.ubuntu.com/17.10/]("http://releases.ubuntu.com/17.10/")

Good luck and enjoy.

---

### Post by oldfred on 2017-12-10
A lot of newer Dell have needed Dell UEFI updates and NVMe SSD firmware updates. Even if new system. So check you have latest.
Samsung SSD updater does not work well from Linux, use Windows if Samsung SSD.

       Dell UEFI Dual boot instructions using Something Else
[https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN](https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN)
[https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en](https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en)

Possible similar models.

 Dell XPS 13 9360 
[https://ubuntuforums.org/showthread.php?t=2353288](https://ubuntuforums.org/showthread.php?t=2353288)
Dell XPS 13 9560 install without issues
[https://ubuntuforums.org/showthread.php?t=2357321](https://ubuntuforums.org/showthread.php?t=2357321)
[https://wiki.archlinux.org/index.php/Dell_XPS_15_9560](https://wiki.archlinux.org/index.php/Dell_XPS_15_9560)
Dell XPS 13 9360 16.04 worked after nvme firmware & BIOS update, 16.10 did not, new rEFInd for NVMe
[http://askubuntu.com/questions/884991/ubuntu-16-10-dual-boot-error-grub-efi-amd64-signed-package-failed-to-install](http://askubuntu.com/questions/884991/ubuntu-16-10-dual-boot-error-grub-efi-amd64-signed-package-failed-to-install)
Dell XPS 13 9360 Dualboot Windows 10 and Ubuntu 16.04 AHCI NVMe
[http://askubuntu.com/questions/867488/dell-xps-13-9360-dualboot-windows-10-and-ubuntu-16-04?noredirect=1#comment1344306_867488](http://askubuntu.com/questions/867488/dell-xps-13-9360-dualboot-windows-10-and-ubuntu-16-04?noredirect=1#comment1344306_867488)
Ubuntu 16 on the DELL XPS15 9550 Tutorial
[https://ubuntuforums.org/showthread.php?t=2345444](https://ubuntuforums.org/showthread.php?t=2345444)

---

### Post by mark1904 on 2017-12-16
Hello, I have gotten the Dell XPS 13 with the intel i7-8850U, and so far, the latest stable linux kernel runs well on it.

I am not sure if ubuntu will work because it doesn't have a bleeding-edge kernel like Arch.

But for sure, I think using the latest Ubuntu 17.10 will do just fine. It's probably best to just wait for the new LTS release (18.04).

My setup: [https://ibb.co/hMpj5R](https://ibb.co/hMpj5R)

---

