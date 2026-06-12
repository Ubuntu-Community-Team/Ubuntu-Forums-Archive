---
title: "Dualboot 16.04 with win 10"
date: 2017-07-29
forum: Installation &amp; Upgrades
---

### Post by utinker on 2017-07-29
I am having problems using the 16.04 installer - at first I chose the option to install as dual boot with win 10 but the installer only gives me the option to install it on the HDD. I want to install it on the SSD where win 10 is installed. The installer does not give me that option, it only shows HDD as the place to install as a dual boot.
I went back and chose the option to try something else, but it says no root file is available. I understand that Ubuntu needs a root file, swap file, etc but I'd rather the installer take care of it hence my choosing the first option to install it as a dualboot.

My PC is a Win 10 machine with SSD, HDD, and 8GB RAM. I use the HDD for data only, Win 10 and other programs are stored on the SSD. Can the 16.04 installer install it on the SSD to dual boot with Win 10?

Any help would be appreciated.

---

### Post by igdfpm on 2017-07-29
If you have not manually re-partitioned your W10 SSD it is likely that the W10 partition takes up the entire disc - which is why it is suggesting the HDD with, presumably, some free space available.

If you boot the live OS you should have access to gparted to resize the W10 partition to your liking and allow ubuntu some room ;)

---

### Post by oldfred on 2017-07-29
Did you turn off Windows fast start up? That prevents the Linux NTFS driver from correctly seeing the NTFS partition(s).
Is system UEFI, most newer systems are?

See also link in my signature for UEFI info.

 Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

### Post by utinker on 2017-07-30
interesting replies from both oldfred and igdfpm - windows fast start up is turned off but the installer still does not show the ssd, only the hdd. The whole of ssd is for win 10 but it has available space in the partition (189gb free space). The whole of hdd is for data only with 191gb free space. So both the ssd and the hdd have only one partition each - does that make a difference?

---

### Post by oldfred on 2017-07-30
Should not be an issue, post this:
       sudo parted /dev/sda unit s print

Sometimes just partitioning in advance with gparted and using Something Else works better. It is the only way I install as I do not like letting system go out and install somewhere with whatever sizes it likes.

Is SSD the new NVMe type? If so, it may need new firmware and/or UEFI/BIOS may need update from vendor.

What brand/model system?
Some also need other boot parameters.

---

### Post by utinker on 2017-07-30
System is home built with OCZ Trion100 250?gb SSD (not NVMe) and Seagate 450gb HDD. Win 10 installed on SSD so boots from SSD. HDD is for data only so is not bootable yet ubuntu installer points to it when I chose to install it as dual boot with win 10.

I did try to use 20gb from the SSD as a separate partition and tried to use something else and pointed installer to the 20gb but it said no root file was found so I couldn't do anything else.

---

### Post by oldfred on 2017-07-30
With Something Else and a partition created in advance, you still have to tell it which partition is / (root) as any partition could be root. Use change button, select ext4 and /. If reusing an existing /home partition, you do the same, choose partition, but DO NOT choose format partition as that would erase all your data.

---

### Post by utinker on 2017-07-30
Ok I have created 20gb partition on the ssd in advance and run the ubuntu installer, changed the 20gb partition to ext4 /. That's done, below the list of the different partitions is the device booted from - here it says the ocz ssd, should I leave it there or change it to sda3 (the 20gb) partition? And install Ubuntu after that?

---

### Post by oldfred on 2017-07-30
You always install grub2's boot loader to a drive like sda, almost never to a partition.

If an UEFI install it really does not matter what you say, as it will only add a folder with boot files into the ESP on sda.  If no ESP - efi system partition on sda, then grub will not install.

Some motherboards need settings in UEFI or boot parameter.
What brand/model motherboard?

And are you using CPU's video or have an add in video card. Othen if nVidia or AMD you need nomodeset on first boot or until you install proprietary driver from Ubuntu repository.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

---

### Post by utinker on 2017-07-31
Motherboard is Gigabyte ga-z87m-d3h with 8gb RAM and no graphics card (using cpu graphics).
Left boot device on sda (ssd). Tried to continue with installation but it says I can either go back to partitioning table and create swap file or continue with installing without any swap file. With 20gb partition for Ubuntu and 8gb RAM, should I go for swap file or continue without one?

---

### Post by oldfred on 2017-07-31
I like to have a little swap, but with 8GB of RAM you may never use it.
I typically put a small 2GB swap on HDD, and have / (root) on SSD.

With 17.04 they changed from a swap partition to a swap file inside / for new installs.
You can later configure a swap file if desired.
       17.04 Ubuntu To Begin Making Use Of Swapfiles In Place Of SWAP Partitions
[http://blog.surgut.co.uk/2016/12/swapfiles-by-default-in-ubuntu.html](http://blog.surgut.co.uk/2016/12/swapfiles-by-default-in-ubuntu.html)
no more than 5% of free disk space or 2GiB, whichever is lower.
[https://wiki.archlinux.org/index.php/swap#Swap_file_creation](https://wiki.archlinux.org/index.php/swap#Swap_file_creation)
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by utinker on 2017-07-31
I did change the 20gb partition to ext 4 and /.
 Is / and / (root) the same? Also I think I'll do without the swap and see what happens.

---

### Post by oldfred on 2017-07-31
It is hard to pronounce / , so I clarify by saying / (root). 
Installer should only show / as one of the many partition options.

---

