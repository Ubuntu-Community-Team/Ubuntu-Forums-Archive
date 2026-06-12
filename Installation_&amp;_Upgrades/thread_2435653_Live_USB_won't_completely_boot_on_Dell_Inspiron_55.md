---
title: "Live USB won't completely boot on Dell Inspiron 5591"
date: 2020-01-23
forum: Installation &amp; Upgrades
---

### Post by boxer-craig on 2020-01-23
Good afternoon.

I  am struggling to get Ubuntu 18.04.3 to boot from a USB drive, and after much searching, reading and trying multiple things have gotten to the point I need to ask for some help.

I have a Dell Inspiron 5591 2in1:
Intel i5-10210U Processor
8GB DDR4, 2666MHz
256GB M.2 PCIe NVMe Solid State Drive
Intel(R) UHD Graphics with shared graphics memory


To boot, in the BIOS I have set SATA operation to AHCI (changed from RAID On)
Disabled "Secure Boot"
Fastboot is set to  "Thorough"

With the above settings in the BIOS, the laptop will boot to the CLI boot menu.
I select "Try Ubuntu", but add remove quiet splash and add for the nvme drive.
Here is the GRUB configuration:

[INDENT]set gfxpayload=keep
linux   /casper/vmlinuz file=cdrom/preseed/ubuntu.seed boot=casper nvme_load=YES
initrd   /casper/initrd[/INDENT]

CTRL-x and Ubuntu begins to boot from the USB drive.  All looks to go fine, no error messages while starting, however the computer will stop and not proceed any further.
I'm not certain if what I am seeing as it stopping, is that it begins to load the Graphical interface but nothing is being displayed because at times the screen will go black, other times it wil sit with all the started services displayed but again will not proceed any further.

Any help or suggestions are greatly appreciated.

Thanks
Craig

---

### Post by oldfred on 2020-01-23
Have you updated UEFI and SSD's firmware? Even new systems may need update.

Since very new Dell, you may need 19.10 or even try 20.04.
Note that 20.04 will not be released until April, but I am using it now, even though I still consider my 18.04 LTS my main working install.
When I built this system in 2016, it was several months before 16.04 and I really had to use 16.04 to get it to work well.
But 20.04 will get many updates, if you use it, you may want to reinstall, just to houseclean all the extra update cruft, but do not have to.

May be similar issues even though 7000 series:
Dell 7791 UEFI update & some settings
[https://ubuntuforums.org/showthread.php?t=2431450&page=3](https://ubuntuforums.org/showthread.php?t=2431450&page=3)
Ubuntu 19.10 Provides Good Out-Of-The-Box Support For The Dell XPS 7390 Icelake Laptop
[https://www.phoronix.com/scan.php?page=article&item=dell-xps7390-ubuntu1910&num=1](https://www.phoronix.com/scan.php?page=article&item=dell-xps7390-ubuntu1910&num=1)
[https://www.phoronix.com/scan.php?page=news_item&px=Dell-XPS-7390-More-Options](https://www.phoronix.com/scan.php?page=news_item&px=Dell-XPS-7390-More-Options)
[https://wiki.ubuntu.com/Dell/XPS/XPS-13-7390-2-in-1](https://wiki.ubuntu.com/Dell/XPS/XPS-13-7390-2-in-1)
[https://ubuntuforums.org/showthread.php?t=2431791](https://ubuntuforums.org/showthread.php?t=2431791)

Dell Precision 5530
[https://ubuntuforums.org/showthread.php?t=2420905](https://ubuntuforums.org/showthread.php?t=2420905)
Dell 5230 with 3 m2 drives.
[https://ubuntuforums.org/showthread.php?t=2406057](https://ubuntuforums.org/showthread.php?t=2406057)

---

### Post by boxer-craig on 2020-01-24
Thanks oldfred.

I first tried to boot Ubuntu 19.10 but it failed everytime so also tried 18.04.3.

Under Windows I had previously ran an update check and updates were applied.  Looking deeper there was an UEFI update available (SSD is up to date), did not realise firmware checks were not part of the update check I had done.
I have been able to boot LiveUSB Ubuntu 19.10 flawlesly every time since updating UEFI.

I'm a bit out of touch with Windows as I've also been using a Chromebook the last year and a bit lol.  It has gotten much better for running Linux apps, but stiill too many roadblocks and felt it is time to move on.  Aside from a Supermicro board running EXSI I put together a few years ago, the last machine I built has an i7-3770K at it's heart (no problems running recent Ubuntu of course) and hardware is beginning to fail so I decided to get my first laptop.

I missed one simple step with my checks and greatly appreciate your time and help.

Craig

---

### Post by oldfred on 2020-01-24
You can change to [Solved]

---

