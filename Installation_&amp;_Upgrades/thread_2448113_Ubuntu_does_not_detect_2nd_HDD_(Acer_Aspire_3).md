---
title: "Ubuntu does not detect 2nd HDD (Acer Aspire 3)"
date: 2020-08-02
forum: Installation &amp; Upgrades
---

### Post by JdeS on 2020-08-02
Installing Ubuntu 20.04 (U20). Laptop: Acer Aspire 3, model # A315-56. Laptop comes with 2 disks:
Disk1: 256GB SSD
Disk2: 1TB HDD


Laptop has Win10 on Disk1. Disk2 is empty.


First attempt to install U20 on laptop was not successful due to:
[https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347](https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347)


After following the steps there, U20 finally detected Disk1/SSD and I was able to install Ubuntu on it.


However, the second drive i.e. Disk2, remains hidden to Ubuntu. This disk is not found by lsblk, fdisk, lshw... nothing.


But logging out (from U20) and logging in to Win10, it is there, appearing as a huge 1TB empty hard disk.


Is there a step I missed to get U20 to detect this second HDD?

---

### Post by CelticWarrior on 2020-08-02
Quoting from your own link:
> 
[LIST]
[*]Turning RST off completely in BIOS.
[*]Changing the storage controller protocol from RST to Advanced Host Controller Interface (AHCI).
[/LIST]


This ^^^ is the general recommendation. Did you change the mode to AHCI? Don't forget to install AHCI support in Windows before this change. That done Windows should be booting and working as good as before and all your drives will be visible and usable in Ubuntu.

This should be all, really.

---

### Post by oldfred on 2020-08-02
Does gparted show drive?
If drive gpt partitioned or totally blank, like a new drive?

Acer Aspire A315-53-386P remove RAID from drive
[https://askubuntu.com/questions/1167506/the-installation-window-dont-show-a-root-file-system-for-choose-in-the-installa](https://askubuntu.com/questions/1167506/the-installation-window-dont-show-a-root-file-system-for-choose-in-the-installa)

Issues most common by brand and then if Intel or AMD. So similar models will have same types of issues.
Acer Aspire 5 Model A515-54-5649  Intel Core i5-10210U Install Tutorial
[https://ubuntuforums.org/showthread.php?t=2437702](https://ubuntuforums.org/showthread.php?t=2437702)
Acer Aspire E15 will not dual boot, many details Trust settings in step 35
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot)
Acer Nitro 7 Missing AHCI mode Ctrl + S in UEFI
[https://ubuntuforums.org/showthread.php?t=2429951&p=13900969#post13900969](https://ubuntuforums.org/showthread.php?t=2429951&p=13900969#post13900969)

---

