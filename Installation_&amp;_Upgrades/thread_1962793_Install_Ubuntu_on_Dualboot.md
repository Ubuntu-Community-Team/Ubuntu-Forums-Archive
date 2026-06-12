---
title: "Install Ubuntu on Dualboot"
date: 2012-04-21
forum: Installation &amp; Upgrades
---

### Post by andrw on 2012-04-21
Hi,

I'm trying to install Ubuntu on dualboot, keeping Windows 7 operating system. I have my hard disk splitted into three partitions:
/ dev / sda
    / dev/sda1 (Windows 7 Loader)
    / dev/sda2
    / dev/sda3

I want to install Linux on partition 'sda3'. How should I proceed? In other words, what option should I select for that partition since by definition it is set to "Use as: to not use the partition"? And for "Device for boot loader installation" what option should I select in order to when I to boot the pc I can select which operating system I want to start?

Thanks in advance for your help.
Best regards

---

### Post by DJ_Max on 2012-04-21
What ISO are you using to install Ubunut?

Regardless Ubuntu amd Linux installers all together have gotten a lot better. You should be able to choose the option to install on any partition without windows. Meaning it will install Linux on any partition the installer doesnt recognzie has Windows on it.

You can change the MBR so the laptop boots grub2, where you can choose to boot windows or ubuntu. Or you can not install it and have something like EasyBCD for Windows 7 bootloader

---

### Post by andrw on 2012-04-21
Thanks for your reply, DJ_Max. I'm installing Ubuntu 11.04 Desktop. I am a beginner in the Linux world. Can you tell me the options I must choose in the installer?

---

### Post by darkod on 2012-04-21
You plan to install only on one partition, without swap? Ubuntu usually installs on two partitions, the main system partition called root, and smaller swap partition.

If you want to use only /dev/sda3 for ubuntu, when you click on the Change button you will need to change the Use As to ext4.
Next, select the mount point to /, tick the format box (it should be selected anyway), and that's it.

For the bootloader select /dev/sda, without any number in it.

Note that this will delete all data on sda3 because it will be formatted to ext4. If you want to keep the data on it, you can't use it for ubuntu.

---

### Post by DJ_Max on 2012-04-21
What do you have on /dev/sda2?

---

### Post by andrw on 2012-04-21
darkod, thanks for your reply :) And what if I also want to create a swap partition?

DJ_Max, /dev/sda2 is a system partition created by Windows OS.

Best regards

---

### Post by DJ_Max on 2012-04-21
Ok probably the rescue partition.

Did you create /dev/sda3?

I would use the custom partitioning settins
Anyhow you should delete /dev/sda3. Which leaves that free space.

I believe the installer can setup two partitions itself on the free space for Ubuntu (one for "/" and one for "swap")

If not, you can create these yourself.

---

### Post by andrw on 2012-04-21
Yes, I have created /dev/sda3 partition when I installed Windows for a future installation of Ubuntu, but it is empty. How do I use the default settings? Delete the /dev/sda3 partition, select the free space and click 'Install now' button? Thanks

---

### Post by DJ_Max on 2012-04-21
You should have just left the rest as "free space" rather than creating a partition.

When you do the install choose to use custom partitioning.

---

### Post by darkod on 2012-04-21
You can delete sda3 and let ubuntu use the unallocated space with the auto method.

Or you can install with the manual method for better control. In this case again you can delete sda3, and create root and swap partitions. Better to create them as logical because if you create two new primary it will use the maximum limit of four primary partitions on the disk.

The root partition is usually used with ext4 filesystem, the swap with swap area filesystem. The swap partition has no mount point.

---

### Post by andrw on 2012-04-21
When you say "auto method" it means choosing the option "Install Ubuntu alongside Windows" instead of option "Something else in this screen?

[IMG]http://www.ubuntu.com/sites/www.ubuntu.com/files/active/installation-type.jpg[/IMG]

Thanks

---

### Post by darkod on 2012-04-21
Yes. That will install on two partitions, root + swap, into the unallocated space dividing it accordingly.

With Something Else you control the exact size of partitions because you create them yourself.

---

### Post by andrw on 2012-04-21
There is only one problem: if I delete the partition and click to go back to the previous menu the elimination of the partition is aborted.
Do I have to manually create partitions? How much space should I allocate to swap partition?

Thanks a lot for your help.

---

### Post by DJ_Max on 2012-04-21
Yes create the two partitons
Swap something lime RAM + 2GB
/ whatever is left

If it were already unallocated space you wouldnt have to do this

---

### Post by darkod on 2012-04-21
You don't manage partitions with the installer, unless you want to use the manual way. So, you can delete sda3 and create new ones.
You can't try to delete it and quit the process, it will not save changes if you quit.

If you simply want to delete it, boot into live mode (not install mode), and use Gparted. Then you can start the install process.

As for swap size, depending how much space you have to allocate to ubuntu. If you don't have too much space, make swap 2GB or similar. Note that if you want to hibernate you will need swap around 1.5 x RAM. Otherwise, you can make it 2GB especially if you have plenty or RAM. No need to waste space on swap it will rarely be used with loads of RAM.

---

### Post by andrw on 2012-04-22
Done! Thank you so much for your help :)

---

