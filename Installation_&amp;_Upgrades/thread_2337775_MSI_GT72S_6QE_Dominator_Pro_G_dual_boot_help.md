---
title: "MSI GT72S 6QE Dominator Pro G dual boot help"
date: 2016-09-21
forum: Installation &amp; Upgrades
---

### Post by jacekkenji on 2016-09-21
Hi there!
Recently I have bought my new laptop, a glorious MSI GT72S 6QE Dominator Pro which came with a pre installed windows 10. Since I want to make some cool stuff (tensorflow) with this laptop, apart from gaming, I wanted to install a Linux distro (ubuntu or whatever else) alongside windows.
So I made an usb with the ubuntu installation, made some research on the matter and tried all the different settings in the BIOS in order to install the linux distro.
The laptop has a 2 SSD hard drives in RAID mode and windows is installed on them.
Problems: 
* first if I start my pc in UEFI mode then during the installation i have a warning (the warning: another os installed in "Bios compatibility mode" if you continue you may not be able to access the other os) and if I continue the ubuntu installation is unable to even see the SSD hard drives (it only see the HDD ) 

* if I start in legacy mode then during the installation I don't see the warning but still ubuntu is unable to detect the SSD hard drives 

* If I switch the sata mode from RAID to AHCI then ubuntu is able to see the SSD drives but it seems that there is no partition table. 

* in every attempt I made ubuntu was always unable to recognize the installed windows 10 and so I never had the option to "install alongside windows"


ps: I tried with Ubuntu 14LTS, Ubuntu 16LTS and LinuxMint 18. Same results with all of them. 
pps: I have disabled fast boot, secure boot and intel speedSomething as I have read that they interfere with the installation process 
ppps: link to the specs [https://www.amazon.co.uk/gp/product/B01FBXEBLE/](https://www.amazon.co.uk/gp/product/B01FBXEBLE/)

Any tips or help would be greatly appreciated! 
Thanks!

---

### Post by oldfred on 2016-09-21
Your RAID is part of the issue.
With 12.04, the desktop had no RAID support, only server and an alternative installer which included all the RAID & LVM tools from server version but in a desktop version. But alternative was discontinued, stating they would include RAID & LVM in desktop version. LVM is now fully supported but RAID is only partially there as near as I can tell. Another part of RAID issues is there are many types of RAID, BIOS(fakeRAID), software ware , and many different hardware RAID cards needing unique drivers.

Some other threads:
 [SOLVED] MSI GT72S 6QE - Freezes on boot unless acpi=off is used
[http://ubuntuforums.org/showthread.php?t=2303544](http://ubuntuforums.org/showthread.php?t=2303544)
MSI GS60 2QE 2xSSD RAID 0 + 1TB HDD dual boot w8.1/w10 problem 
[http://ubuntuforums.org/showthread.php?t=2297815](http://ubuntuforums.org/showthread.php?t=2297815)
MSI PX60 2qd 034us Haswell & Optimus libata.force=noncq for SSD hangup
[http://ubuntuforums.org/showthread.php?t=2296878](http://ubuntuforums.org/showthread.php?t=2296878)
MSI gaming laptop [SOLVED] Dual Boot Ubuntu 14.04 & Windows 8, Ubuntu won't boot
[http://ubuntuforums.org/showthread.php?t=2218742](http://ubuntuforums.org/showthread.php?t=2218742)
[http://ubuntuforums.org/showthread.php?t=2271540&p=13260387#post13260387](http://ubuntuforums.org/showthread.php?t=2271540&p=13260387#post13260387)
Recommended "libata.force=noncq"
[http://ubuntuforums.org/showthread.php?t=2298912](http://ubuntuforums.org/showthread.php?t=2298912)

---

### Post by jacekkenji on 2016-09-21
Thank you for your answer.

I have already read all your linked posts and it seems that nobody actually installed ubuntu alongside windows without reinstalling windows itself in AHCI mode.

Do you know if any new release of Ubuntu (or other linux distro) has support for this RAID setting of mine?

Is there a driver for Ubuntu that can be installed in order to make the RAID recognizible by Ubuntu? If so, is it possible to install the necessary driver during a live session of Ubuntu and then install it alongside windows?

Thank you in advance!

---

### Post by oldfred on 2016-09-21
Possibly related, but I think it is more a driver issue for Intel SRT type RAID.

  Warning: Microsoft Signature PC program now requires that you can't run Linux. Lenovo Yoga 900 ISK2 UltraBook Sept 2016
[https://ubuntuforums.org/showthread.php?t=2337719](https://ubuntuforums.org/showthread.php?t=2337719)
[https://hardware.slashdot.org/story/16/09/21/1516230/microsoft-signature-pc-requirements-now-blocks-linux-installation-reports#comments](https://hardware.slashdot.org/story/16/09/21/1516230/microsoft-signature-pc-requirements-now-blocks-linux-installation-reports#comments) 

Several years ago users turned RAID off, removed RAID meta-data, installed Ubuntu and turned it back on. With those systems it was not BIOS or FakeRAID, but Intel SRT. Not sure what you have.

If RAID, have you tried the server installer? It is not a live installer, but includes many RAID drivers.


 [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
dmraid was replaced by mdadm for handling FakeRAID in Ubuntu 14.04.
15.04 or later now uses mdadm to support intel fakeraids 
User who installed fakeRAID
How to install Ubuntu 14.04 in software fakeraid RAID 1 with Intel Z87 chipset mobo controller
[http://ubuntuforums.org/showthread.php?t=2229126](http://ubuntuforums.org/showthread.php?t=2229126)

---

