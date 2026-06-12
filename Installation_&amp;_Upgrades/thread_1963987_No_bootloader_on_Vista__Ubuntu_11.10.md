---
title: "No bootloader on Vista / Ubuntu 11.10"
date: 2012-04-23
forum: Installation &amp; Upgrades
---

### Post by michael5 on 2012-04-23
Hi,

I installed Ubuntu 11.10 using the pendrivelinux installer (according to [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/#button](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/#button)). I did it by booting from the USB drive, running the pendrivelinux installation program on the ubuntu-11.10-desktop-i386.iso file. 

The installation program said that I'll be able to choose between Vista and Ubuntu on boot so I assumed that it'd install GRUB or a similar bootloader. 

However, when I boot, it's always Vista. If I press F3 during boot, I get to the Vista bootloader and I can only see one option in the list of options and that's Vista. 

When I installed Ubuntu from the USB drive, I chose to install it onto an SD card (a 32 MB SDHC card), which resides on drive H:. Don't know if that is the problem or anything else...

Anyone?

/Michael

---

### Post by darkod on 2012-04-23
I am little confused. The pendrivelinux installer is used to prepare a bootable usb so you can boot and try it in live mode, or install.

You do not actually do the installation with the pendrivelinux like you said it, you only create the usb stick.

Are you sure you actually did a full ubuntu installation, or you only prepared the usb stick?

Also, for more details of the system, you can run the boot info script from the link in my signature. Post the results as explained there. That will show more details of what you have. Run the script with the SD card plugged in.

---

### Post by michael5 on 2012-04-23
Sorry about the confusion. Yes, I ran Ubuntu from the USB stick, played around with it and then chose to install it. And I installed it onto the SD (H) drive. 

Does that make it more clear?

Best,
Michael

---

### Post by darkod on 2012-04-23
Yeah, but we still need the script results to have more details.

Did you try to boot from the SD card? If the grub2 bootloader was installed on the card you need to boot from it, not from the hdd.

---

### Post by ronaldbrijo on 2012-04-23
Ubuntu requires at least 4GB hard drive space, I dont think it actually installed on the 32mb SD card.

I would suggest installing it alongside your Vista and reduce the Vista partition on your HDD.

Regards

---

### Post by michael5 on 2012-04-23
> **ronaldbrijo said:**
> Ubuntu requires at least 4GB hard drive space, I dont think it actually installed on the 32mb SD card.

I would suggest installing it alongside your Vista and reduce the Vista partition on your HDD.

Regards

:) sorry it's a typo again from my side (tired today). It's a 32 GB card. Gigabytes. 

I used the default partitioning that was suggested so that around half was dedicated for the OS and the other half for files. So around 15-16 GB each for the two partitions. 

/Michael

---

### Post by michael5 on 2012-04-23
> **darkod said:**
> Yeah, but we still need the script results to have more details.

Did you try to boot from the SD card? If the grub2 bootloader was installed on the card you need to boot from it, not from the hdd.

I think this might be the problem. As far as I can see, there's no way to boot from it. However, from the BIOS I do indeed have an option to boot from "Removable media" which I guess includes the USB port(s) AND the SD card. Or perhaps it's just not possible to boot from the card slot? It's an ASUS F5 Entertainment System, Dual Core Intel 1.7 GHz computer. 3 years old. 

That was what I thought GRUB would fix, in other words let me boot from anywhere, for example the "removable media" slot (SD card). But if GRUB was put on the SD card, then I have a kind of catch 22 don't I?

/Michael

---

### Post by westie457 on 2012-04-23
Hi.

With the SD  card plugged in boot your computer and check the settings in the BIOS. If the card is recognized there you will be able to set the BIOS to boot from it. However if it is not recognized then there is no way to boot from it un less you have an adapter that accepts SDcards and allows you to plug into a USB port.

---

### Post by michael5 on 2012-04-23
Do you think I should run Ubuntu form the USB stick (pendrive) again and reinstall? 

If so, how do I ensure that GRUB is installed this time then?

---

### Post by darkod on 2012-04-23
First make sure to double check whether the card is recognized, and whether you can boot from it or not, as suggested above.

If there is no way to boot from it, one option is installing grub2 to the internal hdd, BUT that would mean you will not be able to boot the computer without the card.

Only a small part of the bootloader goes to the MBR of the hdd. This part has information where are its config files, to continue the boot. If the card is not there so that grub2 can find its config files, it will not boot both ubuntu and windows. Don't think that it will boot windows because it is installed on the internal hdd. Grub2 will need its config files present.

If the problem is booting from the card, I can't see what improvement would be to install once more. Unless you decide to put grub2 to the hdd, but you can do that from live mode even without installing. You can use the current installation and just add grub2 to the hdd.

If you decide to do that, we can give you the commands.

---

### Post by michael5 on 2012-04-23
> **darkod said:**
> First make sure to double check whether the card is recognized, and whether you can boot from it or not, as suggested above.

If there is no way to boot from it, one option is installing grub2 to the internal hdd, BUT that would mean you will not be able to boot the computer without the card.

Only a small part of the bootloader goes to the MBR of the hdd. This part has information where are its config files, to continue the boot. If the card is not there so that grub2 can find its config files, it will not boot both ubuntu and windows. Don't think that it will boot windows because it is installed on the internal hdd. Grub2 will need its config files present.

If the problem is booting from the card, I can't see what improvement would be to install once more. Unless you decide to put grub2 to the hdd, but you can do that from live mode even without installing. You can use the current installation and just add grub2 to the hdd.

If you decide to do that, we can give you the commands.


Well, I booted and entered the BIOS with a USB stick and the USB stick was identified as removable media but not the SD card, so I guess the BIOS doesn't recognize the SD card slot. 

Perhaps the BIOS can be upgraded, it's American Megatrends version 2.0.59. But I guess not. 

The main hard disk has two partitions, one with Vista and another one with documents. I guess I could put the documents on the SD card and use the second hard disk partition for Ubuntu instead.

The documents are backed up on Google Docs so it doesn't matter if the SD card would break down.

---

### Post by darkod on 2012-04-23
The choice is yours.

Just so there is no misunderstanding, you don't have to reinstall on the hdd. It should work from the SD card as long as the bootloader is on the hdd so that BIOS can read it.

If you want to try only installing the bootloader to the hdd first, boot into live mode with the stick, open terminal and post the output of:
sudo fdisk -l (small L)

---

### Post by techsupport on 2012-04-23
> **michael5 said:**
> Well, I booted and entered the BIOS with a USB stick and the USB stick was identified as removable media but not the SD card, so I guess the BIOS doesn't recognize the SD card slot. 

Perhaps the BIOS can be upgraded, it's American Megatrends version 2.0.59. But I guess not. 

The main hard disk has two partitions, one with Vista and another one with documents. I guess I could put the documents on the SD card and use the second hard disk partition for Ubuntu instead.

The documents are backed up on Google Docs so it doesn't matter if the SD card would break down.

I don't think you have Vista installed on the SD card.  Backup what you want to keep from Vista onto the SD card.  Shrink the Vista partition with Ubuntu Gparted.  Install Ubuntu side-by-side on the actual physical hard drive. You may want to hunt around youtube for a actual tutorial on how to install Ubuntu on Vista. Something like that might be more helpful. ):P

---

### Post by darkod on 2012-04-23
> **techsupport said:**
> I don't think you have Vista installed on the SD card.  Backup what you want to keep from Vista onto the SD card.  Shrink the Vista partition with Ubuntu Gparted.  Install Ubuntu side-by-side on the actual physical hard drive. You may want to hunt around youtube for a actual tutorial on how to install Ubuntu on Vista. Something like that might be more helpful. ):P

If he wants to keep ubuntu on the SD card, why all this??? Plus, resizing with Gparted is risky when Disk Management in Vista can do the job. Windows prefers the system partition to be resized with its own tool, if possible. In XP there was no such tool apart from third party software, but since Vista the Disk Management can resize the partitions.

---

### Post by michael5 on 2012-04-23
> **darkod said:**
> The choice is yours.

Just so there is no misunderstanding, you don't have to reinstall on the hdd. It should work from the SD card as long as the bootloader is on the hdd so that BIOS can read it.

If you want to try only installing the bootloader to the hdd first, boot into live mode with the stick, open terminal and post the output of:
sudo fdisk -l (small L)

Thanks. I would like to put it on the SD card if possible because then I dont have to change the other stuff. 

Here's the output from fdisk -l:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
251 heads, 63 sectors/track, 19767 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x405e966c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    16386047     8192000   1c  Hidden W95 FAT32 (LBA)
/dev/sda2   *    16386048   172675071    78144512    7  HPFS/NTFS/exFAT
/dev/sda3       172675072   312580095    69952512    f  W95 Ext'd (LBA)
/dev/sda5       172677120   312580095    69951488    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 2063 MB, 2063073280 bytes
16 heads, 32 sectors/track, 7870 cylinders, total 4029440 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32     4029439     2014704    6  FAT16

Disk /dev/sdc: 31.9 GB, 31914983424 bytes
255 heads, 63 sectors/track, 3880 cylinders, total 62333952 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e64d8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        8192    32936673    16464241    c  W95 FAT32 (LBA)
/dev/sdc2        32937982    62332927    14697473    5  Extended
/dev/sdc5        58404864    62332927     1964032   82  Linux swap / Solaris
/dev/sdc6        54476800    58396671     1959936   82  Linux swap / Solaris
/dev/sdc7        32937984    50546687     8804352   83  Linux
/dev/sdc8        50548736    54474751     1963008   82  Linux swap / Solaris

Partition table entries are not in disk order

/Michael

---

### Post by darkod on 2012-04-23
OK. From live mode in terminal try:
```
sudo mount /dev/sdc7 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

That will install grub2 on the MBR of /dev/sda. Reboot and you should see the grub2 boot menu.

---

### Post by techsupport on 2012-04-23
> **darkod said:**
> If he wants to keep ubuntu on the SD card, why all this??? Plus, resizing with Gparted is risky when Disk Management in Vista can do the job. Windows prefers the system partition to be resized with its own tool, if possible. In XP there was no such tool apart from third party software, but since Vista the Disk Management can resize the partitions.

I've used Gparted plenty of times to resize Vista partitions, no issues or problems. Ubuntu doesn't really require that much space on a hhd to be completely installed either.  And grub (had?) issues with SD cards a while ago, maybe not anymore, but...  Yeah, you can resize the Windows partitions in Vista instead.  That will work too. Why not just use something like VMware and virtualize Ubuntu in Windows? You can migrate that Ubuntu virtualized image to the SD card instead. You can even then use the SD card on different hardware that is running VMWare software. More flexible. I think that would be better than just trying to run Ubuntu from an SD. Better for the long-term too, imho.  Virtualization is the way to go with something like this.

---

### Post by michael5 on 2012-04-23
> **darkod said:**
> OK. From live mode in terminal try:
```
sudo mount /dev/sdc7 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```That will install grub2 on the MBR of /dev/sda. Reboot and you should see the grub2 boot menu.

Scary :)

sdc7 is the SD card, right?

And the grub command installs grub onto the main hard disk (sda) boot partition, right?

What if the SD card is removed? Someone said I cannot boot Vista then, because grub would rely on /dev/sdc7 being available. Or...?

/Michael

---

### Post by techsupport on 2012-04-23
> **michael5 said:**
> Scary :)

sdc7 is the SD card, right?

And the grub command installs grub onto the main hard disk (sda) boot partition, right?

What if the SD card is removed? Someone said I cannot boot Vista then, because grub would rely on /dev/sdc7 being available. Or...?

/Michael

That's why I am recommending that you install VMWare in Windows and install Ubuntu virtually in VMWare. Migrate your Ubuntu image to the SD card and even run it from there. You can even unplug the virtualized Ubuntu image that will eventually be migrated on the SD and plug it into another computer Ubuntu/Mac/Windows that has VMware Player & still use it virtually to boot your Ubuntu.  Try virtualization. I can't imagine speed being a consideration since you are thinking about installing Ubuntu on a SD card to begin with. You can try it.

---

### Post by darkod on 2012-04-23
> **michael5 said:**
> Scary :)

sdc7 is the SD card, right?

And the grub command installs grub onto the main hard disk (sda) boot partition, right?

What if the SD card is removed? Someone said I cannot boot Vista then, because grub would rely on /dev/sdc7 being available. Or...?

/Michael

Yes, I said that.

If you can't boot from the card your options are limited.

Then you would have to consider to install ubuntu on the hdd.

Or run it as a VM as suggested but that will influence the speed, and might not be the way you want to use it also. Depemding how exactly you set the VM you have two OSs running at the same time and consuming resources instead of one.

---

### Post by michael5 on 2012-04-23
> **darkod said:**
> Yes, I said that.

If you can't boot from the card your options are limited.

Then you would have to consider to install ubuntu on the hdd.

Or run it as a VM as suggested but that will influence the speed, and might not be the way you want to use it also. Depemding how exactly you set the VM you have two OSs running at the same time and consuming resources instead of one.

But let's say that I'd get a crash on the SD card and the data is wiped, or if the SD card is removed. Then I at least want to be able to boot Vista. Isn't the problem solved, if that would happen, by inserting another (empty) SD card? To work as a kind of "dummy". Or are files written to the SD card which are read by GRUB? Does it write anything absolutely vital for it so it doesn't at least offer the option to boot into Vista...!?

/Michael

---

### Post by darkod on 2012-04-23
Yes, it does write "vital" configuration files without which it will not boot. There will only be a grub error on boot.

So, you have to sit down, and make a decision. From what you have told us so far, it seems the options are:
1. Keep vista on the hdd, ubuntu on the SD as it is now. Put grub2 on the hdd. The computer won't boot without the SD plugged in.
If anything happens to it, that means the whole ubuntu installation is lost anyway. You can get a new SD, install ubuntu again and the computer keeps working with vista on the hdd available.
In worst case, you can make vista boot even without installing ubuntu again or getting a new SD. From ubuntu live mode, all you need to run is two commands and vista can boot on its own.

2. Install ubuntu on the hdd. That way the computer is bootable without the SD. You will need to sit down and plan the space on the hdd. If the vista partition is full, you need to move some of the data, and then shrink the partition to make unallocated space in which you will install ubuntu.

3. Install ubuntu in a VM, like inside Virtual Box or VMware for example. I don't know how exactly VMware works, but if it's similar to Virtual Box that means it is not a real dual boot, just a virtual ubuntu inside windows. If windows fails, you can't run ubuntu either. That is not the case with a proper dual boot where they are independent. Also, your resources are not really used well because windows will have to boot, you will have to open Virtual Box as a program and then start ubuntu as a virtual machine. All of that is running at the same time using up cpu and memory much more than only ubuntu would.

These are the three basic options that I can think of.

I think you worry too much about the SD and option 1. So, just keep it in the computer, who cares. Until it totally breaks down, you can use it like that. And as I said above, even if it completely fails you can add a generic mbr on the hdd with linux tools, not to mention that you can make right now a vista rescue cd which will be able to restore the windows bootloader on the hdd if you ever need it.

---

### Post by michael5 on 2012-04-25
> **darkod said:**
> Yes, it does write "vital" configuration files without which it will not boot. There will only be a grub error on boot.

So, you have to sit down, and make a decision. From what you have told us so far, it seems the options are:
1. Keep vista on the hdd, ubuntu on the SD as it is now. Put grub2 on the hdd. The computer won't boot without the SD plugged in.
If anything happens to it, that means the whole ubuntu installation is lost anyway. You can get a new SD, install ubuntu again and the computer keeps working with vista on the hdd available.
In worst case, you can make vista boot even without installing ubuntu again or getting a new SD. From ubuntu live mode, all you need to run is two commands and vista can boot on its own.

2. Install ubuntu on the hdd. That way the computer is bootable without the SD. You will need to sit down and plan the space on the hdd. If the vista partition is full, you need to move some of the data, and then shrink the partition to make unallocated space in which you will install ubuntu.

3. Install ubuntu in a VM, like inside Virtual Box or VMware for example. I don't know how exactly VMware works, but if it's similar to Virtual Box that means it is not a real dual boot, just a virtual ubuntu inside windows. If windows fails, you can't run ubuntu either. That is not the case with a proper dual boot where they are independent. Also, your resources are not really used well because windows will have to boot, you will have to open Virtual Box as a program and then start ubuntu as a virtual machine. All of that is running at the same time using up cpu and memory much more than only ubuntu would.

These are the three basic options that I can think of.

I think you worry too much about the SD and option 1. So, just keep it in the computer, who cares. Until it totally breaks down, you can use it like that. And as I said above, even if it completely fails you can add a generic mbr on the hdd with linux tools, not to mention that you can make right now a vista rescue cd which will be able to restore the windows bootloader on the hdd if you ever need it.

As a Vista rescue disk solves that problem, I think I'll go ahead with the original alternative, to put Ubuntu on the SD. 

Cheers and thanks for the great tips.

Michael

---

