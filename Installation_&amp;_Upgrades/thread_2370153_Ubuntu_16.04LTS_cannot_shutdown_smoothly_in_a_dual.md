---
title: "Ubuntu 16.04LTS cannot shutdown smoothly in a dual boot"
date: 2017-08-31
forum: Installation &amp; Upgrades
---

### Post by ruwan2 on 2017-08-31
Hi,

My new Dell XPS 8900 PC cannot install Ubuntu 16.04 at first for its video card issue. After using procedures below link, it is successfully installed along with Windows 10.

[https://ubuntuforums.org/showthread.php?t=2303880&highlight=Dell+XPS+8900](https://ubuntuforums.org/showthread.php?t=2303880&highlight=Dell+XPS+8900)

At the last step of Ubuntu installation, it asks for restart. When I enter it, it has an error, saying something: ACPI Error:  [\_SB_.PCIO.XHC_.RHUB.HS11] Namespace lookup failure.
AE_NOT_FOUND (20160930/dswload-210)

[http://tinypic.com/r/28unx4g/9](http://tinypic.com/r/28unx4g/9)
......


I force it shutdown by press the PC power button. When restart PC, if I select Ubuntu at GRUB, it can load, and shutdown normally. The problem is if I select Windows 10, it thinks the hard drive has some problems to check it. After it repairs the supposed problems on System Partition, Ubuntu cannot shutdown normally. It continuously prints some printk message saying pcieport ...

[http://tinypic.com/r/xfawyr/9](http://tinypic.com/r/xfawyr/9)


That is, Windows 10's voluntarily reparation changes something on the system partition.

Could you help me on correct the problem?


Thanks,

---

### Post by ruwan2 on 2017-08-31
Below links show the message when Windows 10 runs after Ubuntu installed:

[http://tinypic.com/r/2vrsmcm/9](http://tinypic.com/r/2vrsmcm/9)
[http://tinypic.com/r/2agq1r4/9](http://tinypic.com/r/2agq1r4/9)

---

### Post by oldfred on 2017-08-31
See post #15 on user who reported error & updated UEFI and documented his UEFI settings.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1584407](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1584407)

Have you added AHCI driver in Windows and changed to AHCI?
Does your system have NVMe drive(s)?

       Dell XPS 13 9360 16.04 worked after nvme firmware & BIOS update, 16.10 did not, new rEFInd for NVMe
[http://askubuntu.com/questions/884991/ubuntu-16-10-dual-boot-error-grub-efi-amd64-signed-package-failed-to-install](http://askubuntu.com/questions/884991/ubuntu-16-10-dual-boot-error-grub-efi-amd64-signed-package-failed-to-install)
Dell XPS 13 9360 Dualboot Windows 10 and Ubuntu 16.04 AHCI NVMe
[URL="http://askubuntu.com/questions/867488/dell-xps-13-9360-dualboot-windows-10-and-ubuntu-16-04?noredirect=1#comment1344306_867488"]http://askubuntu.com/questions/867488/dell-xps-13-9360-dualboot-windows-10-and-ubuntu-16-04?noredirect=1#comment1344306_867488
[/URL]
 Dell with NVMe needs AHCI & boot option nvme_load=YES
[https://www.dell.com/support/article/us/en/19/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en](https://www.dell.com/support/article/us/en/19/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en) 

[URL="http://askubuntu.com/questions/867488/dell-xps-13-9360-dualboot-windows-10-and-ubuntu-16-04?noredirect=1#comment1344306_867488"]
[/URL]

---

