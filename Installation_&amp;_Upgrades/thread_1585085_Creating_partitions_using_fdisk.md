---
title: "Creating partitions using fdisk"
date: 2010-09-30
forum: Installation &amp; Upgrades
---

### Post by regsethu on 2010-09-30
Hi,

I am a beginner to Ubuntu and Linux in general. I have a dell poweredge 2950 server which had red hat on it. I have installed ubuntu on top of it. I have replaced master boot record during the installation of ubuntu as I dont want use red hat anymore. 
During the installation it asked me for the space I wanted to give for Ubuntu and I provided 10GB. 
Now I can use only 10GB of my harddrive until I mount other partitions correct?

So when I type sudo fdisk -l I get the below printed:

```
Disk /dev/sda: 146.2 GB, 146163105792 bytes
255 heads, 63 sectors/track, 17769 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c873a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          32      248832   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2              32       17770   142485505    5  Extended
/dev/sda5              32       17770   142485504   8e  Linux LVM

```

I dont know what Linux LVM means. I know I have 2 harddisks both 150GB in a RAID configuration. So may be it means that.

Now I want to create logical paritions in my Extended partition and then mount that to a directory so that I can use that space. Is this the only way to access the remaining space?

When I try 
sudo fdisk /dev/sda 
then type n to create a new partition 
then type l to create a logical partition 
it throws an error saying No free sectors available.

Please tell me how can I access the remaining spaces in my harddisk?

---

### Post by srs5694 on 2010-09-30
You don't have a RAID configuration, or at least not a software RAID configuration. (It's possible you've got a hardware RAID controller that's presenting two or more disks as /dev/sda.)

What you *do* have is a Logical Volume Manager (LVM) configuration. In LVM, disk space is allocated in logical volumes instead of or in addition to being allocated in partitions. LVMs can span multiple hard disks, much like RAID configurations, so it's conceivable that your existing LVM covers multiple disks. Logical volumes appear in the /dev/mapper directory:

```

$ ls /dev/mapper
control       nessus-g_root  nessus-opt   nessus-usr
nessus-emu    nessus-g_usr   nessus-root  nessus-usrlocal
nessus-g_opt  nessus-home    nessus-swap

```

Check to see if you've got logical volumes defined like this. (If not, they may need to be activated by typing "sudo vgchange -ay". If you don't have a vgchange program, you must install it by typing "sudo apt-get install lvm2" or by using a GUI such as Synaptic.)

If your Red Hat LVM is working, I recommend using it rather than repartitioning; LVM is much more flexible. You can manipulate logical volumes by using a range of text-mode tools or by using the kvpm or system-config-lvm GUI tools. (Chances are you'll have to install these programs.) If you've got existing data from your Red Hat installation, you can mount the relevant logical volume like you would a partition. For instance, if you had exactly the same logical volumes as I've got (shown earlier), you might type "sudo mkdir /mnt/oldhome; sudo mount /dev/mapper/nessus-home /mnt/oldhome" to mount the old nessus-home logical volume on /mnt/oldhome.

Precisely what you do with the disk space beyond this is up to you; you can delete old logical volumes, create new ones, resize them, etc. Googling "Ubuntu LVM" turned up quite a few hits, but I'm not sure which one provides the best advice. A few years ago, I wrote a three-piece series on RAID and LVM for Linux Magazine. Part 1 is [here](http://www.linux-mag.com/id/2453) and Part 3 is [here.](http://www.linux-mag.com/id/2577) (Free registration required. Part 2 is on RAID and so isn't important for you.)

---

