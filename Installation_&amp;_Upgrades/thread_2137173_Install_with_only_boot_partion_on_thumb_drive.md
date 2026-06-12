---
title: "Install with only /boot partion on thumb drive"
date: 2013-04-19
forum: Installation &amp; Upgrades
---

### Post by superdaveozzborn on 2013-04-19
I am trying to setup an older PC (Yes it can boot to USB) with Ubuntu and have only the /boot partition on a USB Thumb drive. Not running the operation system from the USB but to have the OS installed on the internal HDD and only the /boot on the USB Thumb drive, I do not want to run the operating system from the USB Thumb drive.

What i would like to do is. plug in the thumb drive and boot the computer and login.
If no thumb drive is plugged in when the computer is turned on, it will not boot up due to the lack of a /boot partition.

After many attempts I have been able to get it to work, BUT .... after a kernel upgrade the system will no longer boot to the desktop but only dumping into (initramfs) prompt with a warning that UUID=blablablabla does not exist, which is the thumb drive. doing a blkid command will show the thumb drive in the list but only with a different UUID. 

so then I decided to try using the label of the thumb drive instead of the UUID in the fstab, this produces the same results after doing a kernel upgrade.

I can reboot the system all day long as long as i do not upgrade it.

I just don't get it.

I have searched Google / Yahoo many many times for the past week now, trying different variations of boot from USB with no luck, perhaps I'm just not wording it correctly?

Any one know of a guide or perhaps how to do this?
Any help would be greatly appreciated. Thank You.

---

### Post by oldfred on 2013-04-20
I would not put /boot, but just grub and maybe just the grub in the MBR of the flash drive. And leave /boot inside your install's / (root) partition.

From your install you can just install grub2's boot loader to any drive. If flash drive is sdb.
       #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub

    
Or you can create a grub only bootable flash drive. All my flash drives have grub. But you have to manually maintain the grub.cfg file. I use grub on flash drives (and now hard drive) to boot ISO directly.

 Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)
Label partition & mount:
sudo grub-install --root-directory=/media/grub2 /dev/sdb
[https://wiki.archlinux.org/index.php/GRUB2#Booting_an_ISO_Directly_From_GRUB2](https://wiki.archlinux.org/index.php/GRUB2#Booting_an_ISO_Directly_From_GRUB2)

      
 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
Older thread
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

As above you can have a simplied grub entry that does not require maintenance when kernel is updated.
      
 I first saw this from Ranch hand
Note that this does not define the kernel. It defines the partition. It boots the newest bootable kernel that it finds at that partition. example based on sda13 change all 13's to your partition number.
At least for Ubuntu family OS's, they all place symlinks in /, called vmlinuz and initrd.img These point to the most recent versions of the kernel in the /boot folder.
More info:
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

   menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}

---

### Post by superdaveozzborn on 2013-04-20
This is perfect, I was not wording it correctly then, this is exactly what i was wanting to do.

Thank You

---

### Post by oldfred on 2013-04-20
Glad you got it working. :)

---

