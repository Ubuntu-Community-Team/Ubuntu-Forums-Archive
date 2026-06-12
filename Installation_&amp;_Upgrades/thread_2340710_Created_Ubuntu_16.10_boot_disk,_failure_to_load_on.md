---
title: "Created Ubuntu 16.10 boot disk, failure to load on duel boot system"
date: 2016-10-21
forum: Installation &amp; Upgrades
---

### Post by aagnathist on 2016-10-21
Hello all,
    I'm a new Linux user, and trying to create a duel boot system with Windows 10 already installed. 
I've had a couple of issues so far. To start, system properties are:

Motherboard Model: MSI MS-1795
Total Memory Size: 8 GBytes
Processor Name: Intel Core i7-6700HQ
Video Chipset: NVIDIA GeForce GTX 960M
Video Chipset: Intel HD Graphics 530
Monitor Name: Chi Mei [Unknown Model: CMN1735]
Drive Model: SanDisk SD8SNAT256G1122
Drive Model: HGST HTS721010A9E630
Drive Model: TSSTcorp CDDVDW SU-208GB
Audio Adapter: Intel Skylake PCH-H - High Definition Audio Controller
Network Card: Intel Dual Band Wireless-AC 3165
Network Card: Qualcomm/Atheros e2400 PCI-E Gigabit Ethernet Controller

After system boot I get: [http://imgur.com/pCTrK9Y](http://imgur.com/pCTrK9Y), [http://imgur.com/CTv28ac](http://imgur.com/CTv28ac) (says "Try Ubuntu without installing.")
After I select either "Try Ubuntu without installing" or "Install Ubuntu" I get: [http://imgur.com/svhAGHe](http://imgur.com/svhAGHe)
It will run its lights at the bottom there and then stops and will sit there for at least ten hours (that's as long as I could wait).
If I select "e" to edit on either options, I get: [http://imgur.com/6F5xgdL](http://imgur.com/6F5xgdL), [http://imgur.com/w9UktV3](http://imgur.com/w9UktV3)
I could use some help on this one guys. Thanks for taking a look.

---

### Post by yancek on 2016-10-21
With windows 10 installed, it is probably using UEFI so you need to boot the Ubuntu medium UEFI and install UEFI.  Some details on that at the Ubuntu documentation site below which you should read before trying.  All the images you posted are what is expected.  What is not expected is it taking 10 hours and not booting.  Read the link below.  Also, did you download the Ubuntu iso from the official site?  Did you do an md5 checksum to verify the download?  Have you tried booting the DVD/flash drive on another computer to test it?

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2016-10-21
You have nVidia, so you probably need nomodeset.
Skip BIOS boot screens:
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) 

 MSI-Z97/Intel's Core i7 5775C Broadwell Is Running Well On Ubuntu 15.10 Iris Pro 6200
[http://www.phoronix.com/scan.php?page=article&item=ubuntu-1510-bdw&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu-1510-bdw&num=1)
MSI Z170
[http://askubuntu.com/questions/801841/dual-boot-ubuntulatest-and-windows-10-on-msi-h170m-pro-vdh-using-msi-click-bio/802095#802095](http://askubuntu.com/questions/801841/dual-boot-ubuntulatest-and-windows-10-on-msi-h170m-pro-vdh-using-msi-click-bio/802095#802095) 
Older MSI needed this:
 Disable MSI Z87 fast boot to get it to work
[http://ubuntuforums.org/showthread.php?t=2272131&p=13258725#post13258725](http://ubuntuforums.org/showthread.php?t=2272131&p=13258725#post13258725)

With my motherboards I had to change quite a few settings in UEFI.
I turn off Secure boot(Windows or Other), turn on allow USB, set USB to UEFI boot only, make sure drive is AHCI mode, turn off fast boot in UEFI (mine has number of sec delay if fast boot on, which after configuration I set to 3 sec),

Yours will not be identical but should have similar settings:
 Asus-ar screenshots oldfred
[http://ubuntuforums.org/showthread.php?t=2258575&page=2](http://ubuntuforums.org/showthread.php?t=2258575&page=2)

---

### Post by aagnathist on 2016-10-21
Will try UEFI. Downloaded Ubuntu from official site, I do not know what an md5 checksum is, and I do not have another computer to try it on, as I am on business travel. Thank you for your response!

---

### Post by oldfred on 2016-10-21
I missed that it is 960M which is laptop chip, not separate video card.
What model system?

Some MSI laptops:
 Failing to Boot Ubuntu 16.10 in MSI GP72
[http://askubuntu.com/questions/838212/failing-to-boot-ubuntu-16-10-in-msi-gp72](http://askubuntu.com/questions/838212/failing-to-boot-ubuntu-16-10-in-msi-gp72)
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

