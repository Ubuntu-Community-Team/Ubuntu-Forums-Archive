---
title: "Ubuntu and Win 7 partitions new install"
date: 2013-11-23
forum: Installation &amp; Upgrades
---

### Post by npinn001 on 2013-11-23
Hi there,

I have a Windows 8 laptop which is frustrating me no end. Windows 8 frustrates me and I hate this secure boot nonsense. 

I'm going to be installing a copy of windows 7 over it, but when I look at it there are about 10 partitions in all (its a lenovo).

I want to be able to have a 100GB Win 7 Partition, and then install Ubuntu straight after it.

I want to split up the remaining 400GB between an Ubuntu partition and then a storage space for videos and files etc, which Win 7 can access.

My question is, do I need a boot partition when putting Win 7 on there to be able to dual boot, ie:

Boot 1000MB
Win 7 100GB
Ubuntu 20GB
Home 50GB
Swap 4GB
Storage 300GB

Or something like that?? What would you suggest?

Thanks

---

### Post by Allavona on 2013-11-23
Can you disable secure/fast boot in your bios and enable legacyboot?

---

### Post by ptrakk on 2013-11-23
nope i put my /boot/ in my "ubuntu" drive. you just have to link it to your MBR with grub. 

# sudo mkdir /mnt/boot
make empy mount directory

# sudo blkid
display disk partitions

# sudo mount /dev/sdXY /mnt/boot
where X is the letter of the drive and Y is the number of the partition containing the boot/ 

# sudo grub-install --root-directory=/mnt/boot /dev/sdX
notice there is no Y at the end of the previous line.

this can be done from a live cd




if you end up at a grub prompt on boot. set root. specify kernel, specify initrd. perhaps tweak parameters. boot and update-grub.
grub> 
#ls 
#ls (hdX,Y)/
#ls (hdX,Y/boot/
#linux (hdX,Y)/boot/vmlinuz-<somethingheremaybe>
#initrd (hdX,Y)/boot/initrd-<somethingheremaybe>
once you get it running 
#sudo update-grub.

or try [http://askubuntu.com/questions/145241/how-do-i-run-update-grub-from-a-livecd](http://askubuntu.com/questions/145241/how-do-i-run-update-grub-from-a-livecd)

---

### Post by fantab on 2013-11-24
> **npinn001 said:**
> 
I have a Windows 8 laptop which is frustrating me no end. Windows 8 frustrates me and I hate this secure boot nonsense. 
I'm going to be installing a copy of windows 7 over it, but when I look at it there are about 10 partitions in all (its a lenovo).
I want to be able to have a 100GB Win 7 Partition, and then install Ubuntu straight after it.
I want to split up the remaining 400GB between an Ubuntu partition and then a storage space for videos and files etc, which Win 7 can access.

**My question is, do I need a boot partition when putting Win 7 on there to be able to dual boot, ie:**

Boot 1000MB
Win 7 100GB
Ubuntu 20GB
Home 50GB
Swap 4GB
Storage 300GB

Or something like that?? What would you suggest?

I have some followup questions before I answer yours.
1. Does you computer boot in EFI mode? I suspect it does.
If it does boot in EFI mode then you will need a 500mb FAT32 partition with 'boot' flag.

If you have a Ubuntu DVD/USB then boot with it and 'Try Ubuntu without installing". Open Terminal [Ctrl + Alt + T], run the following commands and post its output here:
```
sudo parted -l
sudo fdisk -l
```
The output will tell us what you have and we may help you further.

---

### Post by oldfred on 2013-11-24
You have to decide if you want to keep the current gpt partitioning that Windows only boots with UEFI or convert to the 30+ year old MBR(msdos) partitioning with both Ubuntu & Windows only boot with BIOS boot mode.

You can convert a Windows 7 DVD that only installs in BIOS mode to UEFI.
 Only 64 bit supported for UEFI boot
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
Prepare an usb thumb drive, to boot windows 7 in UEFI mode
[http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177](http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177)
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx)

If you let Windows install in BIOS mode over gpt, it only converts the primary gpt partition table. One advantage of gpt is that it has a backup, but Windows leaves that and then Linux sees both MBR and gpt and gets confused. You have to then remove backup gpt table.

      
 GPT Advantages (older but still valid)  srs5694 post #2:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)

---

