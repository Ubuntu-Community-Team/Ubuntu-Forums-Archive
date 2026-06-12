---
title: "boot problem (SATA)"
date: 2010-09-15
forum: Installation &amp; Upgrades
---

### Post by j'ordos on 2010-09-15
Hello all,

I have an old Athlon XP 1700+ where I wanted to install Xubuntu 10.04 (latest stable release). I have one 80Gb IDE drive with a 10Gb FAT32 partition for Windows 98 SE, and a 70G NTFS partition for Windows XP. Then I have two more IDE drives of 160Gb each for data, partitioned as NTFS. Now my IDE slots are all occupied (I also have a DVD-rom) but my motherboard, an Asrock K7VT4A pro also sports two SATA ports, so I got myself an old 80Gb SATA drive (not SATA II, I checked) and installed it. After some initial trouble to detect the drive (I had to enable a SATA RAID function in the BIOS) and some more trouble to get the xubuntu installer to detect the drive (the solution [here]("http://www.pendrivelinux.com/ubuntu-installer-cant-find-my-sata-drive/") worked) I finally installed Xubuntu successfully, but now it refuses to boot from that Hard drive :( .
On my first install I let it write the GRUB bootloader to the MBR. It didn't detect my Windows 98 install but I figured I'd be able to add that myself. Strangely it wrote the bootloader to the MBR of the SATA drive instead of my main IDE drive so the when I restarted my PC I just got the old windows boot menu. After using the BIOS boot menu I selected the SATA drive and got the GRUB loader. I tried starting Xubuntu from there, but I got an error stating it gave up waiting for the root or something along those lines. I checked the commands in GRUB and it loaded hd(0,1). I changed that into hd(3,1), hd(3,0), hd(4,0), hd(4,1) and hd(0,0) (I think) all to no avail (same error message every time). Selecting the windows option from GRUB took me to the windows boot menu, unfortunately I forgot to take a look at the command it executed for that.
So I reinstalled the whole thing after that, and for some reason decided to skip the GRUB step in the installer. Now when I select the SATA drive from the boot menu it says 'Looking for boot record... OK' and hangs there.

Any ideas? :)

edit: forgot, the SATA drive is auto-partitioned, one ext4 partition and one swap partition of about 3Gb)

---

