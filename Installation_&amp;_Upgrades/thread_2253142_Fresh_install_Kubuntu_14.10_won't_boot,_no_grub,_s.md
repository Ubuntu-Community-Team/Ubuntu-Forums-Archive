---
title: "Fresh install Kubuntu 14.10 won't boot, no grub, straight to black screen"
date: 2014-11-17
forum: Installation &amp; Upgrades
---

### Post by finny388 on 2014-11-17
Just built new machine
Gigabyte H97N-wifi, i5 4590, samsung 840, wd black 4TB, Asus Strix 970

Live USB would go to black screen after grub until I learned to press 'e' and replace 'splash quiet' with 'nomodeset'.

So then I was able to install Kubuntu
sda (840) partitioned 50MB for EFI partition (sda2) and the rest for / (sda1)
sdb (WD 4TB) 8GB for swap (sdb2) and the rest for /home (sdb1)

Now when I try to boot it posts and then 'booting in insecure mode' appears, then screen goes black, a short press on the power button will power it down.

I'm new to EFI and secure boot, I only created the 50MB EFI partition as I was prompted to do so during install
Bootloader was assigned to sda during install
Hacking around to install linux is somewhat nostalgic but more so embarrassing when people ask how I'm loving my new pc.

I suspect I have to do the nomodeset thing again until I can install nvidia drivers but  don't know why grub won't come up.

Any help appreciated.

---

### Post by oldfred on 2014-11-17
Is video card then nVidia?

I just built new UEFI system with Asus AR. I had to change a lot of settings in UEFI/CSM to get it to work.

Your efi partition is a bit small. Windows default is 100MB and we often suggest 300MB or a bit more. I do like to have a working install on every hard drive, just to make it easy to boot when something unexpected happens. But I also have a full UEFI boot install on a flash drive also.

My nVidia is an old card as I wanted to test the internal Intel video. But I guess I selected the wrong motherboard as my monitor only has DVI or VGA and motherboard has HDMI and Displayport. :(
So I installed my nVidia 620gt card and was surprised it has worked without issue. My older still nVidia 9600GT always required nomodeset until I installed the nVidia driver from the repository. All live boots and first boot after install.

Best to see details. Post link to summary report.
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)


Note that I have not yet fully partitioned either SSD nor hard drive. 

```
fred@trusy-ar:~$ sudo parted -l
[sudo] password for fred: 
Model: ATA Samsung SSD 840 (scsi)
Disk /dev/sda: 128GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name    Flags
 1      1049kB  525MB   524MB   fat32           efi     boot
 2      525MB   527MB   2097kB                          bios_grub
 3      527MB   26.7GB  26.2GB  ext4            trusty
 4      126GB   128GB   2000MB  linux-swap(v1)


Model: ATA WDC WD10EZEX-00B (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  525MB   524MB   fat32              msftdata
 2      525MB   527MB   2097kB                     bios_grub
 3      527MB   26.7GB  26.2GB  ext4
 4      26.7GB  446GB   419GB   ext4
 5      446GB   476GB   29.9GB  ext4


```

My sdb3 is for another install, not yet done, my sdb4 is for data ( I do not have a lot), and sdb5 is backup from sda, mostly just /home settings as all data is in my data partition on sdb. My data gets backed up, partially to another computer, DVD, flash drives and where ever. :)

I include a bios_grub incase I want to experiment with BIOS boot mode. And sdb1 is FAT32 but boot flag not set yet to be the efi partition for all installs on hard drive. My old hard drive had at least 10 mostly obsolete test installs, just because I had space for another 25GB / (root) partition for next test.

---

### Post by finny388 on 2014-11-17
Thanks Fred, yes the Asus Strix 970 is nVidia.
I followed steps from the Graphics Resolution sticky in this section. This worked:

Booted with live usb and:
```

sudo mount /dev/sda1 /mnt

sudo mount -o bind /dev /mnt/dev
sudo mount -o bind /sys /mnt/sys
sudo mount -t proc /proc /mnt/proc

sudo chroot /mnt /bin/bash
```

found grub file in etc/default

opened with sudo
```
sudo kate grub

```
commented out the GRUB_HIDDEN_TIMEOUT=0 line (put an # at far left of line)

saved grub file

```
sudo update-grub

```
rebooted

voila, there's my grub menu

hit enter, same thing, black screen

try again only this time replace 'quiet splash' with 'nomodeset'

and voila 2, kubuntu booted.

sheesh.

So far so good although in the Additional Drivers section it is not detecting anything but that is another topic. Once I get the video driver installed I'll see if this will reboot without intervention and report back.

---

### Post by finny388 on 2014-11-17
Had to install nVidia drivers from edgers ppa.
Once that was done booting was smooth.
Marking as ridiculous and solved. ;)

---

