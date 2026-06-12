---
title: "Windows 10 not listed in boot directory on UEFI device after ubuntu installation"
date: 2016-02-10
forum: Installation &amp; Upgrades
---

### Post by komali2 on 2016-02-10
Windows 10 is missing from my boot list on my UEFI machine after I installed ubuntu in an empty partition. How can I get it back? 


I used a liveUSB of ubuntu to install ubuntu to an empty partition I had created by shrinking the main partition within Windows 10. The machine is a Lenovo y500. Ubuntu boots fine, but Windows is missing from the boot menu, see[ this image]("http://i.imgur.com/R3rd8br.jpg"). 


I ran update-grub, which yielded the following, rebooted, and found it did not work. 


```
    Generating grub configuration file ...
    Found linux image: /boot/vmlinuz-3.19.0-15-generic
    Found initrd image: /boot/initrd.img-3.19.0-15-generic
    Found memtest86+ image: /boot/memtest86+.elf
    Found memtest86+ image: /boot/memtest86+.bin
    Found Windows Recovery Environment (loader) on /dev/sda1
    done





```

Then, I followed the steps on [an askubuntu]("https://help.ubuntu.com/community/Boot-Repair#A2nd_option_%3a_install_Boot-Repair_in_Ubuntu") link on running a boot repair which yielded [this pastebin. ]("http://paste.ubuntu.com/15010441/")I restarted, and found it did not work. 






fdisk -l yielded the following: 
```

Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0xfe621785

Device     Boot      Start        End    Sectors   Size Id Type
/dev/sda1  *          2048     206847     204800   100M  7 HPFS/NTFS/exFAT
/dev/sda2           206848 1850200063 1849993216 882.1G  7 HPFS/NTFS/exFAT
/dev/sda3       1952600064 1953521663     921600   450M 27 Hidden NTFS WinRE
/dev/sda4       1850202110 1952600063  102397954  48.8G  5 Extended
/dev/sda5       1850202112 1943949311   93747200  44.7G 83 Linux
/dev/sda6       1943951360 1952600063    8648704   4.1G 82 Linux swap / Solaris

Partition 5 does not start on physical sector boundary.


Partition table entries are not in disk order.
```

Thank you for taking a look.

---

### Post by komali2 on 2016-02-10
Solved, the windows recovery option in the boot menu booted windows without issue.

---

### Post by oldfred on 2016-02-10
Grub has not been updated to search for new version of Windows. The os-prober tries to do a match on versions, and then if not found assumes it is the recovery partition.

Best to never boot into a recovery partition as sometime just booting into it, changes partition table entries, removing Linux entry in table. 

       One way to fix the descriptions is to move the windows entries to 40_custom and edit at will.
[http://askubuntu.com/questions/659528/grub-menu-with-windows-10-and-ubuntu-14-04/659910#659910](http://askubuntu.com/questions/659528/grub-menu-with-windows-10-and-ubuntu-14-04/659910#659910)

   Copy the  entries from this:
sudo cp -a /boot/grub/grub.cfg /boot/grub/grub.cfg.backup
gedit /boot/grub/grub.cfg
Copy them to and edit to have only entries you want:
gksudo gedit /etc/grub.d/40_custom
sudo nano /etc/grub.d/40_custom
Then do:
sudo update-grub

   gksudo gedit /etc/default/grub
#Add this line:
GRUB_DISABLE_OS_PROBER=true
sudo update-grub

---

