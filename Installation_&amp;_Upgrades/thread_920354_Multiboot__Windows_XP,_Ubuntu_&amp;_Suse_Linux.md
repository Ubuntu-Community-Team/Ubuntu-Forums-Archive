---
title: "Multiboot  Windows XP, Ubuntu &amp; Suse Linux"
date: 2008-09-15
forum: Installation &amp; Upgrades
---

### Post by Vikram K on 2008-09-15
Hi,

I am totally new to Linux.
I want to install Windows XP Professional, Ubuntu 8.04 LTS & Suse Linux Enterprise 10 in my Laptop.

My Laptop's config are as follows:  320 GB HDD / Intel 2.2Ghz Dual Core / 2 GB RAM.

Please explain me how to Install all the three Operating Systems in my Laptop.

Which OS I should Install first?
How to partition the HDD to install all these Operating Systems?

Please let me know the step by step procedure.

Thanks in advance.

---

### Post by cdtech on 2008-09-15
Your new to Linux? How did you hear about Ubuntu/Suse? Why would you want all that on your laptop? Do you have a lot of hair?

---

### Post by Elfy on 2008-09-15
Personally I would install in this order - xp, suse then ubuntu - only, however because I'm not sure how suse deals with it's bootloader :)

When you install xp - it will iirc have a basic partition setup so you cna just allocate part of the 320Gb to it and leave the remainder of the disc as unallocated.

Download and then burn as an iso partedmagic - [http://partedmagic.com/](http://partedmagic.com/) - you can then boot with this once xp had been installed an updated.

USe it to do the rest of the partitioning - you will need 2 partitions to install suse and ubuntu, a swap partition and then use the remainder to use for data. 

You will have to make an extended partition as you can only have 4 primary partitions on a hdd.

I would make 2 12Gb partitions for the installs, a 2Gb partition for swap and then the rest for the data

---

### Post by prshah on 2008-09-15
> **Vikram K said:**
> 
I want to install Windows XP Professional, Ubuntu 8.04 LTS & Suse Linux Enterprise 10 in my Laptop.

Which OS I should Install first?
How to partition the HDD to install all these Operating Systems?

Please let me know the step by step procedure.


While there are too many steps involved in this, here's a general run-down; this assumes there is no existing OS installed on the laptop.

First, install XP Pro. When asked where to install XP, delete all the partitions, and create a 15-20Gb partition, and choose to install XP onto that (it will be called "C:" drive.)

Next boot off the Ubuntu live CD and make a backup copy of the mbr with ```
sudo dd if=/dev/sda of=/root/mbrbackup bs=446 count=1
``` Copy the file created ("/root/mbrbackup") to a usb penrive and/or to your windows partition as created above. Don't install ubuntu at this point.

Now boot off the Suse disk, and proceed with installation; create a single "primary" partition of 10~15 Gb and give it a mount point of "/" (root) and a single primary 2.2~2.5Gb swap partition; complete the installation.

You can create one more mbr backup at this point as shown before.

Now boot off the ubuntu live CD and run through the installation; 

a) create an extended partition that occupies the rest of the available disk space
b) create a 10Gb "logical" partition (type ext3, mount point "/") to hold ubuntu
d) use the rest of the space to create a type ext3 "/home" partition.
e) for swap, use the partition as created earlier, don't create a fresh one. (Ubuntu should automatically use it, no additional steps required).

To access the "/home" partition in Windows, you can use [Ext2/3 IFS drivers]("http://fsdrivers.org").

You can play about with windows partition size as you like, reducing "/home" size accordingly.

---

### Post by caljohnsmith on 2008-09-15
> **prshah said:**
> 
Next boot off the Ubuntu live CD and make a backup copy of the mbr with ```
sudo dd if=/dev/[COLOR="Red"]sda1[/COLOR] of=/root/mbrbackup bs=446 count=1
```
I think that is a small typo, Prshah, and it will unfortunately profoundly affect the intended purpose of that command. :) To back up the MBR, you should use "sda" and not "sda1", since using sda1 will copy the first 446 bytes of the boot sector of sda1. I believe the correct command is:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] of=/root/mbrbackup bs=446 count=1
```
That of course assumes he has only one HDD.

---

### Post by prshah on 2008-09-16
> **caljohnsmith said:**
> I think that is a small typo, Prshah, and it will unfortunately profoundly affect the intended purpose of that command. :) To back up the MBR, you should use "sda" and not "sda1", since using sda1 will copy the first 446 bytes of the boot sector of sda1. I believe the correct command is:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] of=/root/mbrbackup bs=446 count=1
```
That of course assumes he has only one HDD.

Yes, that's right, it _is_ an error and (now) corrected in my post. Thanks for pointing this out. Your command is correct, and I have changed my post to reflect that.

---

### Post by meindian523 on 2008-09-16
When I did this,I already had XP Pro and Ubuntu installed and 10 GB of HDD space to play with to test out other OSs.I installed openSUSE 11.0,but told it not to install the bootloader.

On rebooting,I booted into Ubuntu,mounted openSUSE's / partition and copied the entried for SUSE from it's menu.lst which had been created(surprisingly for me) and pasted it into Ubuntu's menu.lst and voila.Full post in my blog....not much different from this post,but some precautions to be taken and a warning about the partitioner inbuilt into the openSUSE installer....

---

