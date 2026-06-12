---
title: "Installation of Ubuntu to single partition"
date: 2014-06-09
forum: Installation &amp; Upgrades
---

### Post by tjmlandi on 2014-06-09
So I currently have windows 8.1 installed to an ssd, and a 1.5 tb hdd for storage. I am currently trying to install ubuntu to a partition of the hdd and am having issues. When booting from a usb ubuntu boot drive, it seems I am supposed to get some sort of dual boot or boot alongside option but all I get are Erase All Data, and Something Else. When I select the something else I proceed to a list of partitions, it will not allow me to select the partition I made for ubuntu to install onto, it seems to be dead set on having me fully erase either of my drives. I don't know what to do, and if there is any more specific information needed, I'll gladly provide it.

---

### Post by Bucky Ball on 2014-06-09
*Thread moved to **Installation & Upgrades**.*

Welcome. Better off here. As you're new, people will be gentle. ;)

How did you make the partition and what is the filesystem? If it is not an EXT* partition, not going to happen. You need free space/unallocated space where you want to install Ubuntu (or an EXT* partition).

When you get to the 'Something Else' to manually partition, if you don't have an EXT* partition to use, you are going to need to erase one of the partitions (no doubt an NTFS or FAT partition) to leave free space. You will probably need two partitions so if you are not using EFI you are limited to four partitions per physical disk. To get around this, create an extended partition in the free space and then install to the logical partition '/' for the OS and '/swap' (2Gb fine) for the /swap partition. You will find these in there as default mountpoints. You don't need to do much else but set up the partitions and the install will know where to put things. Good luck.

PS: You can have as many logical partitions inside an extended partition as your hardware will take (and that would be plenty) so you really aren't limited to one partition. You're only limitation is how much free space you have. You may even be able to create the logical partition /home, which can be very handy if you are needing to upgrade/reinstall later on. (Your data is stored in /home and not in the directory /home inside the operating system partition /, if that makes sense.)

---

### Post by tjmlandi on 2014-06-09
I used MiniTool for the partition, and then disk management to make it free space when someone told me it needed to be so

---

### Post by Bucky Ball on 2014-06-09
In that case, you should see the free space when you click 'Something Else' and can then follow the steps in my previous post and create /, /swap (and /home if space permits). What might be preventing this is if you are not using EFI and already have four partitions on the drive already (excluding the free space) ...

The partitions you create should be EXT4, incidentally, which you will also find as a default in the manual partitioning section when you are creating a partition (except the /swap which you choose 'swap space' for, or something like that ... you'll see it there as an option).

---

### Post by tjmlandi on 2014-06-09
Ok, so I put the 2gb /swap and / patartions, and it went through the whole install process, everything seemed fine. However, when it rebooted at the end, when it booted up my BIOS wouldn't recognize the drive to boot into, not sure what happened. Thank you for the help so far, and if at any point, you recognize a problem for which there is a guide to send me to so I don't have to take up too much of your time,  feel free to send me there.

---

### Post by Bucky Ball on 2014-06-09
Your BIOS couldn't find the drive/partition? If you mean you set it to boot the drive that Ubuntu and Win are installed on and it gave an error, what was the error exactly?

Either way, I suggest you try Boot Repair and see if it works. There are two methods; booting a LiveCD and installing/running it there or creating a Boot Repair bootable CD. Your choice.

[https://help.ubuntu.com/community/Boot-Repair#Getting_Boot-Repair](https://help.ubuntu.com/community/Boot-Repair#Getting_Boot-Repair)

PS: I am presuming you are installing in Legacy and not EFI. Please correct me if wrong. ;)

---

### Post by tjmlandi on 2014-06-09
By that I mean, when I opened the setup menu, the only options I had were the ssd and the hdd, which I normally have, and I when I try to boot into the hdd where the ubuntu partition should be, I just get the blinking underscore you get when booting into a drive without an OS. Also, I am using UEFI to boot, it's a new MoBo and I don't even know where the Legacy/UEFI option is in the BIOS yet.

---

### Post by Bucky Ball on 2014-06-09
Did you try Boot Repair, as suggested in my previous post? If it doesn't work, please post a link to the bootinfoscript that Boot Repair outputs.

---

### Post by tjmlandi on 2014-06-09
I tried boot repair. I got to a part where it wanted me to copy and paste some commands into terminal, but after running the commands, the repair wouldn't continue saying the GRUB was still there. Here is the boot repair info I got [http://paste.ubuntu.com/7618534/](http://paste.ubuntu.com/7618534/)

---

### Post by oldfred on 2014-06-09
You have both Windows & Ubuntu booting in BIOS mode from MBR(msdos) partitioned drives.

But you installed grub2's boot loader to sdb7 a partition, where BIOS systems only boot from a MBR. you need to install grub2's boot loader to sdb. Do not use Boot-Repairs auto fix as it will also install grub to sda and you really want to keep the Windows boot loader in sda.
You need to use the advanced mode in Boot-Repair and choose Ubuntu and choose sdb as the location to install grub into.

---

