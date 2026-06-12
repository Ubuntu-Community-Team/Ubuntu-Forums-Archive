---
title: "Cannot UEFI boot into Ubuntu 16.04LTS after installation"
date: 2018-04-04
forum: Installation &amp; Upgrades
---

### Post by jimmyallnighter on 2018-04-04
I have been bashing my head against a brick wall all day trying to get this sorted out.

I'm trying to install Ubuntu 16.04LTS on an SSD from a Live USB.

My hardware specs are as follows:

CPU: AMD Ryzen 1700X
RAM: 32GB Corsair HyperX
Motherboard: MSI X370 SLI
GPU: NVIDIA GTX1080Ti
Disk: Samsung EVO 250GB SSD

All other disks attached are data only and do not have any operating system installed.

This is what happens:

I boot up the live image and install Ubuntu seemingly without a problem.

When I reboot and attempt to load the installation, I get this:

```
error: failure reading sector 0xbbeb40 from `hd2`
alloc magic is broken at 0xd2add2c0: d29bf400
Aborted. Press any key to exit.
```

I then try and use boot-repair (various combinations of settings), but it does restore GRUB, the system still can't boot and still returns an error similar to above. There's also concern that it may be causing the corruption of the GPT partition table (shown in GParted).

Here is the output of lsblk

```
sdf      8:80   0 931.5G  0 disk 
&#9500;&#9472;sdf1   8:81   0   750G  0 part 
&#9492;&#9472;sdf2   8:82   0 181.5G  0 part 
sdb      8:16   1  14.7G  0 disk 
&#9492;&#9472;sdb1   8:17   1  14.7G  0 part /cdrom
sde      8:64   0   1.8T  0 disk 
&#9500;&#9472;sde2   8:66   0   1.8T  0 part 
&#9492;&#9472;sde1   8:65   0   128M  0 part 
loop0    7:0    0   1.7G  1 loop /rofs
sdc      8:32   0   1.8T  0 disk 
&#9500;&#9472;sdc2   8:34   0    50G  0 part 
&#9500;&#9472;sdc3   8:35   0    50G  0 part 
&#9492;&#9472;sdc1   8:33   0   1.7T  0 part /media/mint/Storage
sda      8:0    0 232.9G  0 disk 
&#9500;&#9472;sda2   8:2    0     1K  0 part 
&#9500;&#9472;sda5   8:5    0   232G  0 part /mnt/boot-sav/sda5
&#9492;&#9472;sda1   8:1    0   976M  0 part
```

sda is the disk I'm aiming to install Ubuntu on. It would be nice if I could get btrfs working, but it's no biggie if I can't.

I'm starting to think it might be the new graphics card or motherboard that's causing problems. Maybe it's not fully supported by linux yet?

I'm happy to provide more details on request. Please help!

**UPDATE**

Apparently I was setting the EFI partition size too high. After setting it to 200mb, setting the boot and esp flags and installing with the default options, I got the installation to work. It still displays errors, such as: Environment block too small. However they are usually not fatal during startup.

---

### Post by oldfred on 2018-04-04
Your hd2 could be sdb or sdc.
Drives from BIOS/UEFI and in grub are hd0, hd1 etc.
But many make flash drive hd0 and then assign the internal drives. So hd0 may not be sda. You have to experiment to know your system.

Have you tried unplugging all the other drives?
Or you may just need fsck on whatever partition has issue.
Are all drives gpt?

       To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

One user with newer nVidia cards like yours, in UEFI changed settings to use internal video and connected to motherboard video port. Not sure if same with AMD, as that user had Intel. Then after install, added nVidia driver, reset UEFI for external video,  and rebooted.
You probably need the ppa for newest nVidia driver.

To see available drivers:
ubuntu-drivers devices
 [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
sudo apt-add-repository ppa:graphics-drivers/ppa 
   # should show newest versions available in addition
ubuntu-drivers devices

---

