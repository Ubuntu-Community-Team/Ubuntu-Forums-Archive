---
title: "Install Ubuntu 16.04.2 on Dell XPS 13"
date: 2017-06-02
forum: Installation &amp; Upgrades
---

### Post by caro.hsg on 2017-06-02
When trying to install Ubuntu 16.04.2 on a new Dell XPS 13, I get the error message, "You need at least 8.6 GB to install Ubuntu. You have 0.00 GB available." I have a 256 GB SSD with nothing extra installed.
I realize this is a Dell/Windows problem, but does anyone out there know about this?
Help would be much appreciated.
Thanks in advance....

---

### Post by QIII on 2017-06-02
Hello!

Have you used the Windows Partition Manager to shrink the Windows partition to give yourself some room for the Linux partitions?

---

### Post by caro.hsg on 2017-06-02
No, I haven't done that because I was going to use the entire disc for Ubuntu; not interested in keeping Windows. I've installed Ubuntu on 3 other computers that originally had windows & had no problems.
I'll try that.
Thanks

---

### Post by oldfred on 2017-06-02
Have you turned off RAID in UEFI and set AHCI mode for drive?

Are you installing in UEFI or BIOS  boot mode.
How you boot install media UEFI or BIOS is then how it installs.

 Dell UEFI Dual boot instructions using Something Else
[https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN](https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN)
Dell XPS 13 9360 
[https://ubuntuforums.org/showthread.php?t=2353288](https://ubuntuforums.org/showthread.php?t=2353288)
Dell XPS 13 9560 install without issues
[https://ubuntuforums.org/showthread.php?t=2357321](https://ubuntuforums.org/showthread.php?t=2357321)
Dell XPS 13 9360 16.04 worked after nvme firmware & BIOS update, 16.10 did not, new rEFInd for NVMe
[http://askubuntu.com/questions/884991/ubuntu-16-10-dual-boot-error-grub-efi-amd64-signed-package-failed-to-install](http://askubuntu.com/questions/884991/ubuntu-16-10-dual-boot-error-grub-efi-amd64-signed-package-failed-to-install) 


Older threads.
        Dell XPS 8910  16.04.1 works, 16.04 did not
[URL="https://ubuntuforums.org/showthread.php?t=2351949"]https://ubuntuforums.org/showthread.php?t=2351949
[/URL]
 Dell XPS 13 9343 Needs /EFI/Boot/Bootx64.efi to boot
[http://askubuntu.com/questions/731931/uefi-not-finding-a-bootable-system-on-xps13](http://askubuntu.com/questions/731931/uefi-not-finding-a-bootable-system-on-xps13)
[https://bugs.launchpad.net/dell-sputnik/+bug/1499323](https://bugs.launchpad.net/dell-sputnik/+bug/1499323) 

[URL="https://ubuntuforums.org/showthread.php?t=2351949"]
[/URL]

---

### Post by caro.hsg on 2017-06-02
Got it. THANK YOU

---

