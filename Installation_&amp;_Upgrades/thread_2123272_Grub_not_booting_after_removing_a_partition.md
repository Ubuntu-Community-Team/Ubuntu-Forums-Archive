---
title: "Grub not booting after removing a partition"
date: 2013-03-07
forum: Installation &amp; Upgrades
---

### Post by scottbomb on 2013-03-07
I recently started testing Xubuntu daily builds (for Raring, 13.04) and I'm having an issue with grub. The computer dual-boots Windows 7 and Xubuntu 12.10 (my usual OS). I have about 20GB set aside that's used only for installing the daily builds. In the morning, I download the ISO and install it to the unallocated space using manual partitioning. I let the installer install grub to the default: sda. This makes for a total of 3 operating systems on the machine, 2 versions of Xubuntu and Win 7. 

After testing, I boot into Xubuntu 12.10 (my regular OS) and fire up GParted. I proceed to delete the partition that contained the test installation. I then launch a command prompt and run update-grub. I then go to reboot the computer and it won't boot. It gets stuck at a GRUB> prompt. I have no idea what to do there. The only way I've been able to fix this is by using my Grub Repair CD. How can I prevent this from happening in the first place?

---

### Post by oldfred on 2013-03-07
Better to just install grub to the partition even though that is not recommended. Since there is no option to not install grub, that is about the only choice. It becomes a throw away as you will never use it.

You then can run this to find the new install from your working install.
sudo update-grub

But Ranch hand posted this way back. It boots the partition, so you do not have to update grub on you current install and can just directly boot the new install.

I first saw this from Ranch hand
Note that this does not define the kernel. It defines the partition. It boots the newest bootable kernel that it finds at that partition. example based on sda13 change all 13's to your partition number. Add to 40_custom.
At least for Ubuntu family OS's, they all place symlinks in /, called vmlinuz and initrd.img These point to the most recent versions of the kernel in the /boot folder.
More info:
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}

#Add menu entry to 40_custom, change example from sda13 to your partition.
gksudo gedit /etc/grub.d/40_custom
#Turn off prober
gksudo gedit /etc/default/grub
#Add this line
GRUB_DISABLE_OS_PROBER=true
#update grub menu
sudo update-grub

Full reinstall of grub to MBR.
sudo dpkg-reconfigure grub-pc

---

### Post by darkod on 2013-03-07
On top of oldfred's suggestion, there is a shorter way too.

You can keep doing what you have been doing and let the test version of Xubuntu install grub2 to /dev/sda (the MBR).

BUT, before removing the test partition, boot your main Xubuntu and in terminal run:
sudo grub-install /dev/sda

That will put grub2 from 12.10 back on the MBR and after that you can freely delete the test Xubuntu partition, it will not affect grub2. Maybe you will need to run sudo update-grub to get rid of the test entry after the partition is gone, but the important thing is that the computer will be bootable after deleting the test partition. You only need to remember to do the grub-install from the main partition.

---

### Post by scottbomb on 2013-03-08
Very interesting, thanks guys. I'll be sure to try some of these methods today and over the weekend. It also occurred to be that I probably don't even need to remove the partition, just let the installer over-write it every day with the new build. Nevertheless, I'm on a mission to learn as much Ubuntu as I can so I will be trying these methods anyway.

---

