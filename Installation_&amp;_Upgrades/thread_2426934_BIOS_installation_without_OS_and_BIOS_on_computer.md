---
title: "BIOS installation without OS and BIOS on computer"
date: 2019-09-15
forum: Installation &amp; Upgrades
---

### Post by setonic on 2019-09-15
I bought Dell XPS 2 in 1 (7390) few weeks ago. I was unable to install Ubuntu or run Live, so I started play with BIOS settings. I disabled BIOS self recovery option and after clicked Factory reset BIOS settings - result is - NO BIOS AT ALL. Boot code - 3 yellow lights and 3 white lights says "No BIOS image found".

The question is - how to install BIOS - Dell provides only executable file with BIOS driver. Is there any chance to arise the laptop or now it is a peace of expensive "brick"?

---

### Post by CatKiller on 2019-09-15
[This page](https://www.dell.com/support/article/uk/en/ukbsdt1/sln300716/bios-recovery-options-on-a-dell-pc-or-tablet) might help you.

---

### Post by el_garicimo on 2019-09-20
I also just got the 7390, and am starting to try to figure out how to boot from any usb in general -- any luck? I have some UEFI bootable usb's with various distros on it, and I tried turning the UEFI secure boot off in the BIOS, but then got some message about bitlocker , didn't seem to work...

ha, should have figured trying to get Ubuntu on a brand new laptop wouldn't be easy....even though I've put linux on multiple UEFI devices before!

---

### Post by oldfred on 2019-09-20
All Dell typically need UEFI update & if SSD firmware update.
You need to add AHCI driver into Windows first, then in UEFI change RAID/Intel SRT to AHCI.
You probably have to turn bitlocker off also.

       [URL="https://www.dell.com/support/article/us/en/04/sln151664/how-to-install-ubuntu-linux-on-your-dell-pc?lang=en"]https://www.dell.com/support/article/us/en/04/sln151664/how-to-install-ubuntu-linux-on-your-dell-pc?lang=en
      [/URL]Dell update UEFI/BIOS from Linux
[https://www.dell.com/support/article/us/en/19/sln171755/updating-the-dell-bios-in-linux-and-ubuntu-environments?lang=en](https://www.dell.com/support/article/us/en/19/sln171755/updating-the-dell-bios-in-linux-and-ubuntu-environments?lang=en) 
            [https://www.dell.com/community/Laptops-General-Read-Only/Dell-M-2-FAQ-regarding-AHCI-vs-RAID-ON-Storage-Drivers-M-2-Lanes/td-p/5072571](https://www.dell.com/community/Laptops-General-Read-Only/Dell-M-2-FAQ-regarding-AHCI-vs-RAID-ON-Storage-Drivers-M-2-Lanes/td-p/5072571)
[https://www.dell.com/support/article/us/en/19/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en](https://www.dell.com/support/article/us/en/19/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en) 
    
General UEFI install info in link in my signature below.
 
Other 7000 series. Dell across many models is similar, bigger difference if Intel or AMD based.
       Dell XPS 15 Series 7590 (2019)
[https://askubuntu.com/questions/1161456/how-to-run-ubuntu-on-new-dell-xps-15-7000-series-7590](https://askubuntu.com/questions/1161456/how-to-run-ubuntu-on-new-dell-xps-15-7000-series-7590)
[https://github.com/TillmannBerg/Ubuntu-Dell-XPS-15-2019](https://github.com/TillmannBerg/Ubuntu-Dell-XPS-15-2019)
DELL Inspiron 15 7577 18.04 needed boot parameters
[https://ubuntuforums.org/showthread.php?t=2386049](https://ubuntuforums.org/showthread.php?t=2386049)
Post installation issues Ubuntu 18.04-Dell inspiron 7559
[https://askubuntu.com/questions/1072382/post-installation-issues-ubuntu-18-04-dell-inspiron-7559](https://askubuntu.com/questions/1072382/post-installation-issues-ubuntu-18-04-dell-inspiron-7559)
Dell 7559 Install 16.04 or 18.04, best to skip all 16.04 info
[https://connorkuehl.github.io/dell-inspiron-7559-linux-guide/index.html](https://connorkuehl.github.io/dell-inspiron-7559-linux-guide/index.html)
Dell Inspiron 7566
[https://ubuntuforums.org/showthread.php?t=2342359](https://ubuntuforums.org/showthread.php?t=2342359) 
    [URL="https://www.dell.com/support/article/us/en/04/sln151664/how-to-install-ubuntu-linux-on-your-dell-pc?lang=en"]
[/URL]

---

