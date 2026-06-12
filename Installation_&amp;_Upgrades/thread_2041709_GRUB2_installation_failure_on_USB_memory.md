---
title: "GRUB2 installation failure on USB memory"
date: 2012-08-13
forum: Installation &amp; Upgrades
---

### Post by mibadt on 2012-08-13
Hi,
I intend to create an Ubuntu (12.04 386) based "PC on a Disk on key) as part of my preparation for a long trip.
I took a 32 GB USB memory (Labeled Linux Mint from a former use), booted the PC from a CD, and chose to install on the /dev/sdc (USB memory) and install the grub2 too on that device.
Installation ( with / on sdc1 with NO separate /boot) completed with only a single problem- it reported it couldn't install grub. I completed the installation and rebooted from the CD into a live session with the USB still plugged in.
Somehow I have seen the DOK (disk on Key) icon appearing three times.
I opened a terminal (see below) and, as root, try to reinstall grub which didn't work. I've unmounted the DOK, yet still no success.

Please advise!

Thanks

-----------copy of terminal  (as root)-------------
```


Disk /dev/sdc: 32.0 GB, 32007389184 bytes
255 heads, 63 sectors/track, 3891 cylinders, total 62514432 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003ada6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048    16601087     8299520   83  Linux
/dev/sdc2        16601088    53710847    18554880   83  Linux
/dev/sdc3        60559360    62513151      976896   82  Linux swap / Solaris
/dev/sdc4        53712894    60559359     3423233    5  Extended
/dev/sdc5        53712896    55664639      975872   82  Linux swap / Solaris
/dev/sdc6        55666688    60559359     2446336    b  W95 FAT32

Partition table entries are not in disk order
root@ubuntu:/home/ubuntu# grub-install /dev/sdc
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
root@ubuntu:/home/ubuntu# cd /media/
root@ubuntu:/media# ls
cdrom  Linux Mint 13 Cinnamon 64-bit  Linux Mint 13 Cinnamon 64-bit_  Linux Mint 13 Cinnamon 64-bit__
root@ubuntu:/media# umount Linux\ Mint\ 13\ Cinnamon\ 64-bit
root@ubuntu:/media# ls
cdrom  Linux Mint 13 Cinnamon 64-bit_  Linux Mint 13 Cinnamon 64-bit__
root@ubuntu:/media# umount Linux\ Mint\ 13\ Cinnamon\ 64-bit
umount: Linux Mint 13 Cinnamon 64-bit: not found
root@ubuntu:/media# umount Linux\ Mint\ 13\ Cinnamon\ 64-bit
umount: Linux Mint 13 Cinnamon 64-bit: not found
root@ubuntu:/media# 
root@ubuntu:/media# grub-install /dev/sdc
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).



```

---

### Post by ajgreeny on 2012-08-13
Firstly I don't see why you used the cd /media command , but I'm not sure if that is your problem.
However, try doing the grub-install with the sudo prefix, ie ```
sudo grub-install /dev/sdc
```

EDIT:
Also have a good look at [https://help.ubuntu.com/community/Grub2/Installing#Reinstall_from_the_LiveCD](https://help.ubuntu.com/community/Grub2/Installing#Reinstall_from_the_LiveCD) which suggests that you may need to carry out a slightly more complicated procedure using the live CD; still easy to do but needs more details on where to install grub to.

---

### Post by mibadt on 2012-08-13
Thanks, but that's **exactly as I'v done** (see my terminal) as root.
Anybody else?

---

### Post by oldfred on 2012-08-13
The grub install command is when you are booted into your system. Otherwise you have to mount the install and then install, example is sda5, change all sda5's to your drive & partiiton:

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD/usb, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#  The above command should work but they now suggest this command for grub 1.99 with Natty 11.04 or later - uses boot not root.:
sudo grub-install --boot-directory=/mnt/boot /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# If no errors on previous commands reboot into working system and run this:
sudo update-grub

Many prefer Boot_Repair, now as it is a gui.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

More info if desired:
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

---

### Post by ajgreeny on 2012-08-13
> **mibadt said:**
> Thanks, but that's **exactly as I'v done** (see my terminal) as root.
Anybody else?
OK, I'm not used to seeing users with a root user, hence I didn't notice that fact.

However, you do not appear to have run the mount and grub-install command as shown in that post.
```
sudo mount /dev/sdXY /mnt # Example: sudo mount /dev/sda5 /mnt
sudo grub-install --boot-directory=/mnt/boot /dev/sdX
```Perhaps as you are using a USB which presumably automounts to /media you need to forget about the first command as it will be mounted (check that with **mount** command) and change the second of those two commands to 
```
sudo grub-install --boot-directory=/media/*USBfoldername* /dev/sdX
```details of which I got from [http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)

It may be a different use of a USB, but perhaps the grub installation will be exactly the same.

---

### Post by darkod on 2012-08-13
Since you already mentioned your root partition, lets keep it short:
```
sudo mount /dev/sdc1 /mnt
sudo grub-install --root-directory=/mnt /dev/sdc
```

You will notice I suggested the --root-directory option as opposed to --boot-directory. Even though there are some tutorials that say to use --boot-directory for version 11.04 or later, I have actually seen cases where it didn't work and you had to use --root-directory when you DO NOT have separate /boot.

It seems the --boot-directory option is better to be used but only when having separate /boot partition. In any case you can try them both, and watch out for the difference between /mnt and /mnt/boot.

---

### Post by mibadt on 2012-08-13
Thanks all!

---

### Post by ajgreeny on 2012-08-13
Can we assume this is now solved?
If so can you please:-


[LIST=1]
[*]let us know which was the correct answer for future reference,
[*]mark thread as solved from the **Thread Tools** at the top of the thread.
[/LIST]

---

