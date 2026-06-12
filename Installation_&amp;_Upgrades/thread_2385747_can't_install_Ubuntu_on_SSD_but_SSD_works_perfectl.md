---
title: "can't install Ubuntu on SSD but SSD works perfectly"
date: 2018-02-24
forum: Installation &amp; Upgrades
---

### Post by rouvenster on 2018-02-24
Hello Everyone,

So I have this kind of project for a few months now to rehabilitate my old Acer 5610 laptop. So I wiped out any windows thing inside his guts and upgraded his RAM fro 512MB to 2,5GB.
Second thing I wanted to do was upgrading his HDD to SDD. Problem is, it doesn't have any SATA port. So i bought
this :
[IMG]https://ae01.alicdn.com/kf/HTB1cA0AKFXXXXc1XXXXq6xXFXXXj/221508443/HTB1cA0AKFXXXXc1XXXXq6xXFXXXj.jpg[/IMG]
 [URL="https://www.aliexpress.com/item/Universal-12-7mm-SATA-to-IDE-Optical-Bay-Hard-Drive-Adapter-Caddy-Fit-Slot-Load-ATAPI/32515703782.html?spm=2114.search0104.3.27.242651b97jdRdP&ws_ab_test=searchweb0_0,searchweb201602_4_10152_10151_10065_10344_10068_10342_10343_10340_10341_10084_10083_10618_10630_10307_10313_10059_10534_100031_10103_10627_10626_10624_10623_10622_10621_10620_10142,searchweb201603_36,ppcSwitch_3&algo_expid=e30be51d-464f-4e0d-af30-89856cbece2c-4&algo_pvid=e30be51d-464f-4e0d-af30-89856cbece2c&transAbTest=ae803_5&priceBeautifyAB=0"]https://www.aliexpress.com/item/Universal-12-7mm-SATA-to-IDE-Optical-Bay-Hard-Drive-Adapter-Caddy-Fit-Slot-Load-ATAPI/32515703782.html?spm=2114.search0104.3.27.242651b97jdRdP&ws_ab_test=searchweb0_0,searchweb201602_4_10152_10151_10065_10344_10068_10342_10343_10340_10341_10084_10083_10618_10630_10307_10313_10059_10534_100031_10103_10627_10626_10624_10623_10622_10621_10620_10142,searchweb201603_36,ppcSwitch_3&algo_expid=e30be51d-464f-4e0d-af30-89856cbece2c-4&algo_pvid=e30be51d-464f-4e0d-af30-89856cbece2c&transAbTest=ae803_5&priceBeautifyAB=0
[/URL]
Plugged in a Sandisk SDSSDP-064G And inserted it in instead of my DVDROM drive.
I tried installing linux mint xfce on the HDD and it can see the SSD.  SMART short-test says everything is fine but every statement is flagged as "old-age". Gparted happily format it and create ext4 partition on the whole thing, and I can actually use the media, store stuff inside and everything normally works.

Problem is, when I try to install any Ubuntu flavor on it (all partitions on it or only / )  it always fail with the same message : "The ext4 file system creation in partition #1 of SCSI1 (0,0,0) (sda) failed" and then the whole thing is crashing with tons of errors like "input/output error reading dev/sda". If I press ignore several times I get also "fsync error".
After that, Gparted or Disks are apparently very angry and refuse to detect the SSD and I'm forced to reboot.

At first sight I would say it's hardware failing but I don't understand why I can create partitions and use by myself it but cannot install  OS on it. I mean, is it a boot related issue ? or an Ubuntu-installation issue ? Maybe the installation program can't understand how this drive is connected ? 
Should I try the other SMART scans ?

Thanks for the help

---

### Post by oldfred on 2018-02-24
Some older systems only boot from internal drive, not from a hard drive added to removable drive caddy that is in DVD/CD slot.
And some adapters work better than  others for those systems that do boot from second drive.

Most common work around is to put boot files or boot partition on internal drive and full install on caddy, if caddy otherwise seen.

But using SSD with adapter may give issues as SSD need AHCI for trim to work. Some newer SSD may internally do trim type housecleaning, but most need trim.
And without trim when drive gets "full" (even of deleted data), it will slow down a lot as it has to do housecleaning as it saves new file.

---

