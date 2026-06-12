---
title: "Install from external HD"
date: 2012-04-02
forum: Installation &amp; Upgrades
---

### Post by teddy379 on 2012-04-02
I have an 8GB flash drive and a 500GB USB external HD used for backup. I want to mess around with Ubuntu 12.04 on the 8GB flash drive. So here's what I tried. On Win7 I tried to resize the flash drive into a 700MB partition and the rest into another partition so I can put the Ubuntu ISO installer on the 700 partition and install on the rest of it. It failed. I couldn't actually boot.
I tried to resize the 500GB USB HD and make a small partition to accommodate the Ubuntu installer which didn't boot either. How can I accomplish this without formatting my back up HD?

---

### Post by sudodus on 2012-04-02
> **teddy379 said:**
> I have an 8GB flash drive and a 500GB USB external HD used for backup. I want to mess around with Ubuntu 12.04 on the 8GB flash drive. So here's what I tried. On Win7 I tried to resize the flash drive into a 700MB partition and the rest into another partition so I can put the Ubuntu ISO installer on the 700 partition and install on the rest of it. It failed. I couldn't actually boot.
I tried to resize the 500GB USB HD and make a small partition to accommodate the Ubuntu installer which didn't boot either. How can I accomplish this without formatting my back up HD?
I have made an external HDD bootable and booted linux distros. It boots like a USB flash drive. I used Unetbootin to make it bootable.

I suggest that you format the small partition to FAT32 and add the boot flag and the lba flag. It need not be the first partition, but maybe it should be a primary partition.

For regular booting (of internal drives) linux can boot from a logical partition, but I haven't tried that for a USB drive.

---

### Post by teddy379 on 2012-04-02
> **sudodus said:**
> I have made an external HDD bootable and booted linux distros. It boots like a USB flash drive. I used Unetbootin to make it bootable.

I suggest that you format the small partition to FAT32 and add the boot flag and the lba flag. It need not be the first partition, but maybe it should be a primary partition.

For regular booting (of internal drives) linux can boot from a logical partition, but I haven't tried that for a USB drive.

Gonna try that. I used the Universal Installer along with EASEUS to do the partitioning. I had it set as primary. And I was able to install Ubuntu 9.x about a month ago on a USB flash memory with success.

---

### Post by oldfred on 2012-04-02
If you have an 8GB flash drive why not a full install? I have a full install of 12.04 for testing on a 16GB flash with two 8GB partitions, one for data. Since I have 4GB of RAM I used no swap but will not push it by loading a lot of applications at once.

Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

Procedure is essentially the same for every version.

HOW TO Avoid Wubi & Install Ubuntu on USB Drive -amjjawad
[http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)
HOW TO Install Lubuntu on USB Drive - amjjawad
[http://ubuntuforums.org/showthread.php?t=1872303](http://ubuntuforums.org/showthread.php?t=1872303)

See post #19 C.S.Cameron - recommends disconnection sda so grub can only install to flash drive.
Maverick now only gives combo box on grub location if you use manual install.
Lucid:
[http://ubuntuforums.org/showthread.php?t=1509603](http://ubuntuforums.org/showthread.php?t=1509603)
Step by Step Full install 8GB C.S.Cameron Post #7
[http://ubuntuforums.org/showthread.php?t=1719346](http://ubuntuforums.org/showthread.php?t=1719346)

It does not have to be encrypted BIOS based system:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html]("http://members.iinet.net/%7Eherman546/p19.html")

My system sees flash as a second drive, so install to my 8GB partition on a flash drive is just like any install:
Install to external drive 11.04. Also any second drive.
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")
p24/041.png Shows combo box to select where to install the grub2 boot loader.

---

