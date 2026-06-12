---
title: "Failed to install ubuntu"
date: 2018-12-22
forum: Installation &amp; Upgrades
---

### Post by victor-gao on 2018-12-22
Hi all,
My laptop is xps 13 256 ssd. I tried everything I can and watched a lot of tutorials, but it still stuck at installation type. I was trying to install 18.04 LTS after boot from USB as UEFI MBR. [ATTACH=CONFIG]282000[/ATTACH][ATTACH=CONFIG]282001[/ATTACH].

---

### Post by CatKiller on 2018-12-22
> **victor-gao said:**
> UEFI MBR.

That's a contradiction-in-terms. MBR is for the old-and-crusty BIOS. GPT is the method for the new-and-shiny UEFI.

Boot the LiveUSB in UEFI mode and it will do a UEFI installation. Boot it in Legacy mode and it will do an MBR installation. You can't really mix-and-match.

---

### Post by ubfan1 on 2018-12-22
Do you have Windows installed on the SSD? Is that the only disk?  Did you check it for having basic partitions instead of "dynamic" (You'd need to convert to basic in that case so you could shrink one to make room for Ubuntu ).  Why MBR instead of gpt?  If UEFI Windows is involved, it will have to be gpt, even though Ubuntu would not care.

---

### Post by victor-gao on 2018-12-22
it's really weird that when I burn it as GPT, the boot option from USB is gone.

I did double checked the disc and it is basic, and my laptop only have one disc which is that ssd and windows system installed in it. I just tried GPT, it encountered the same situation.

---

### Post by CatKiller on 2018-12-22
You'll need to boot into Windows and turn off fast boot. Windows hibernates rather than shutting down properly, which leaves the disk inaccessible.

---

### Post by oldfred on 2018-12-22
You need several things with new Dell
You need to add AHCI driver to Windows and then change drive in UEFI from RAID or Intel SRT to AHCI.
You need to update Dell's UEFI and SSD's firmware.
After update you probably need to redo UEFI settings like AHCI, Secure boot off, fast start up off etc.

Just about all recent versions of Dell system use same UEFI. Bigger difference if Intel or AMD chip.
       Dell update UEFI/BIOS from Linux
[https://www.dell.com/support/article/us/en/19/sln171755/updating-the-dell-bios-in-linux-and-ubuntu-environments?lang=en](https://www.dell.com/support/article/us/en/19/sln171755/updating-the-dell-bios-in-linux-and-ubuntu-environments?lang=en)
Dell support - Update on XPS 13/15 2016 Developer Edition availability
[http://en.community.dell.com/techcenter/os-applications/f/4613/t/19670562?pi22229=9](http://en.community.dell.com/techcenter/os-applications/f/4613/t/19670562?pi22229=9)
[URL="http://www.dell.com/support/article/ca/en/cabsdt1/SLN301754/en"]http://www.dell.com/support/article/ca/en/cabsdt1/SLN301754/en
      [/URL]
 Dell UEFI Dual boot instructions using Something Else
[https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN](https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN)
[https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en](https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en)
Dell with NVMe needs AHCI & boot option nvme_load=YES
[https://www.dell.com/support/article/us/en/19/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en](https://www.dell.com/support/article/us/en/19/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en)
[https://www.dell.com/community/Laptops-General-Read-Only/Dell-M-2-FAQ-regarding-AHCI-vs-RAID-ON-Storage-Drivers-M-2-Lanes/td-p/5072571](https://www.dell.com/community/Laptops-General-Read-Only/Dell-M-2-FAQ-regarding-AHCI-vs-RAID-ON-Storage-Drivers-M-2-Lanes/td-p/5072571)
[https://www.dell.com/support/article/us/en/19/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en](https://www.dell.com/support/article/us/en/19/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en)
Dell XPS 13 9560 install without issues
[https://ubuntuforums.org/showthread.php?t=2357321](https://ubuntuforums.org/showthread.php?t=2357321)
[https://wiki.archlinux.org/index.php/Dell_XPS_15_9560](https://wiki.archlinux.org/index.php/Dell_XPS_15_9560)
[https://askubuntu.com/questions/1043842/running-ubuntu-via-live-usb-error-on-dell-xps-15-9560](https://askubuntu.com/questions/1043842/running-ubuntu-via-live-usb-error-on-dell-xps-15-9560) 
    [URL="http://www.dell.com/support/article/ca/en/cabsdt1/SLN301754/en"]
[/URL]

---

### Post by victor-gao on 2018-12-22
Thanks all. Finally, it works. The reason why it won't work is because of the windows works on RAID and Linux works in AHCI. It has to be changed in system configuration under SATA setting.

---

### Post by lpalazzotto on 2018-12-23
For future users: here you can find all the process for Dell Xps 15 clearly explained, with a few nice tips at the end. I think it can easily be used of Xps 13 and most likely other Dell PCs too.

[https://medium.com/@peterpang_84917/personal-experience-of-installing-ubuntu-18-04-lts-on-xps-15-9570-3e53b6cfeefe](https://medium.com/@peterpang_84917/personal-experience-of-installing-ubuntu-18-04-lts-on-xps-15-9570-3e53b6cfeefe)

---

### Post by oldfred on 2018-12-23
Once you install the nVidia driver, you will not want, nor need the nomodeset boot parameter. It may even conflict or prevent use of nVidia driver.

---

### Post by lpalazzotto on 2018-12-23
> **oldfred said:**
> Once you install the nVidia driver, you will not want, nor need the nomodeset boot parameter. It may even conflict or prevent use of nVidia driver.

If you read all the process till the end you would have noticed that nomodeset is indeed removed.

---

