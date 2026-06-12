---
title: "The MBR, Partitions, Boot Loader, etc?"
date: 2008-05-16
forum: Installation &amp; Upgrades
---

### Post by oxsyn on 2008-05-16
I'm trying to understand some basic concepts.  I'd really appreciate a little help filling in the details.

I'll preface the questions with my goal: I've got a laptop.  I want to be able to put on XP, Ubuntu, Slackware & have a shared partition.  I want to use GRUB as the boot loader.

So, here goes.  The way I understand the MBR is that it's a designated bit of space at the very front of the disk that contains information about where the partitions on the disk begin and end.
1.  Is this correct?  Am I missing any important concepts?  
2.  Is there a way to view & edit the MBR?

Now, when I do a linux install, typically there are three necessary partions, the boot partition (usually small, like a few hundred mb), the swap partition (2x your ram) & the partition that contains the operating system and all files (largest).  

1.  What is the bootable partition for?  What kinds of files does it contain and why are they separated from the rest of files?
2.  If you have a dual boot with 2 linux distros, can they share the same swap partition?

Where does the boot loader exist, on the disk?  It can't be on one of the OS partitions, right?  Does it exist on its on little bootable partition?  If I'm using GRUB, can I view and edit it, to configure it the way I want?

Based on my first goal, I'm hoping to have a 20gb XP installation, a 20GB ubuntu installation, a 15 gb slackware installation a 20gb shared partition for documents & a 4gb swap file. (the disk is 80gb) What would be the best way to do this?  

If I install XP pro, it'll take up the whole disk.  If I install ubuntu next, it'll allow me to resize the xp partition, but then the ubuntu install will take up the rest of the disk.

Rather, I assume I should probably use some utility to manually partition the disk, but then I'll need to install & configure grub manually as well, won't I?

In any case, I'm assuming that my disk should probably look something like this when I get done:
| - NTFS (XP) - | BP-U | EXT3 (UB) | BP-SW | EXT3 (SW) | SWAP | FAT32 (SHARED) |

Yes/no?  And if yes, what's the best way to partition it, best order to install the operating systems, and how can I edit GRUB so that it'll allow me to select the OS to boot?

Sorry, I know that's a huge amount of questions.  Thanks in advance.

---

### Post by Rallg on 2008-05-16
Some answers:

You can share swap between several Linux distributions.

The MBR can be viewed and edited by special software (possibly by Midnight Commander from a "System Rescue CD" download). But I wouldn't do it unless absolutely necessary. Instead, I would find software that make a backup copy of your MBR, and fool with the backup if you are curious as to its contents. Any mistake in the MBR is deadly.

Grub can be put on your Ubuntu partition, on your Windows, partition, on external media, or wherever. You can manually edit the menu.lst file, and many users do that. However, starting from the MBR there must be pointers leading to Grub located on a partition that has the "boot flag" (visible in GParted).

If you have Windows XP, you can even manually edit a file for the Windows bootloader to point to Grub, without altering the MBR. Unfortunately Vista does not use the same easy-to-edit file structure.

Manual disk partitioning can be done using GParted from the live CD. There is a maximum of four(?) "primary" partitions allowed. If you have a lot of partitions, you will need to create an "extended" partition which is subdivided into "logical" partitions.

I can't answer your question about the small boot partition, since I boot from external media.

---

### Post by MrEgg on 2008-05-16
> **F4RR4R said:**
> 
1.  What is the bootable partition for?  What kinds of files does it contain and why are they separated from the rest of files?


Creating a /boot partition ensures that grub stage1 will be located below the 1024th cylinder, ie on MBR. Creating a *small* /boot partition makes it less prone to data corruption.

When sizing /boot, keep in mind that it will host all of your kernel boot images (now and future), from all of your linux installs. 100 MB is a usually recommended size for a single install, you may want to add a little more space if you plan to have multiple installs.

HTH,
Egg

---

### Post by oxsyn on 2008-05-16
> **Rallg said:**
> Manual disk partitioning can be done using GParted from the live CD. There is a maximum of four(?) "primary" partitions allowed. If you have a lot of partitions, you will need to create an "extended" partition which is subdivided into "logical" partitions.
Thanks!  I used the Ubuntu Live CD & GPartED to resize & move my partitions.  It's still going right now.

I've got the following partitions now, according to GPartED (or rather, as soon as it's finished):
/dev/sda1 - 22GB,NTFS,boot,WinXP
/dev/sda2 - 22GB,extended *(An extended partition is like a container, that holds other partitions?  Huh?)*
/dev/sda5 - 19GB,ext3 (I thought there was a bootable linux partition somewhere, but I sda2,sda5 &sda6 do not have the boot flag?)
/dev/sda6 - 3GB,linux-swap
New Partition #1 - 14GB,fat32 (i forgot to name it, this will be the shared partition for documents & data)
14GB unallocated (this is where I want to stick my slackware install, but I'm not sure how to do it yet, any suggestions?)

---

### Post by az on 2008-05-16
> **F4RR4R said:**
> The way I understand the MBR is that it's a designated bit of space at the very front of the disk that contains information about where the partitions on the disk begin and end.
1.  Is this correct?  Am I missing any important concepts?  
2.  Is there a way to view & edit the MBR?

The first few hundred bytes of the MBR are executable code.  After which is the partition table.  The executable code is used to allow your computer to find the operating systom on the partition that is maked as bootable and then chainload it.

> **F4RR4R said:**
> 
Now, when I do a linux install, typically there are three necessary partions, the boot partition (usually small, like a few hundred mb), the swap partition (2x your ram) & the partition that contains the operating system and all files (largest).  

No.  You don't need a /boot partition.  Ten years ago, you did because you may have been using a computer that cannot boot a file that is located anywhere but at the beginning of a disk, but this is not so anymore.  And if you chose to use a boot partition and it fills up, you could leave your system unbootable.

Just stick to one root and one swap partition for linux.


> **F4RR4R said:**
> 

2.  If you have a dual boot with 2 linux distros, can they share the same swap partition?

Yes, but if you suspend-to-disk (hibernate) the contents of your ram will be written to your swap, so you should not boot into another linux operating system that will then use the same swap space.

If you don't hibernate, this is not an issue.

> **F4RR4R said:**
> 
Where does the boot loader exist, on the disk?  It can't be on one of the OS partitions, right?  Does it exist on its on little bootable partition?  If I'm using GRUB, can I view and edit it, to configure it the way I want?

If you are using grub, it exists in several places.  One part of it is on your MBR.  There is not enough room there to fit the whole thing, so that part will find the second stage and load that into memory.  The second stage is found on your linux partition.  It is also configured by a text file called /boot/grub/menu.list.

> **F4RR4R said:**
> 
Rather, I assume I should probably use some utility to manually partition the disk, but then I'll need to install & configure grub manually as well, won't I?


Just install Windows and Ubuntu after that.  You can use the ubuntu installer to manually partition your drive any way you want.  It's probably more reliable to use that than a third-party proprietary partitioning program.

> **MrEgg said:**
> Creating a *small* /boot partition makes it less prone to data corruption.


There is no reason to believe that a separate boot will avoid/cause data corruption.

---

### Post by az on 2008-05-16
> **F4RR4R said:**
> 
/dev/sda1 - 22GB,NTFS,boot,WinXP
/dev/sda2 - 22GB,extended *(An extended partition is like a container, that holds other partitions?  Huh?)*
/dev/sda5 - 19GB,ext3 (I thought there was a bootable linux partition somewhere, but I sda2,sda5 &sda6 do not have the boot flag?)


Yes, an extended partition is a container.  The boot flag is only relevant if you are using a typical mbr.  Since Grub will be installed on your MBR, it will locate the second stage and not pay attention to boot flags.

---

### Post by Rallg on 2008-05-16
> 
The boot flag is only relevant if you are using a typical mbr. Since Grub will be installed on your MBR, it will locate the second stage and not pay attention to boot flags.


Some installations (such as mine) do not touch the original MBR. My Grub is on an external USB, which I must select at boot time. Without the USB inserted and selected at boot, the computer will boot directly to the original Windows installation with no knowledge of Ubuntu. In such a case, the boot flag must be present on the Windows OS partition, since the original bootloader is in use.

---

### Post by MrEgg on 2008-05-17
> **F4RR4R said:**
> I've got the following partitions now, according to GPartED (or rather, as soon as it's finished):
/dev/sda1 - 22GB,NTFS,boot,WinXP
/dev/sda2 - 22GB,extended *(An extended partition is like a container, that holds other partitions?  Huh?)*
/dev/sda5 - 19GB,ext3 (I thought there was a bootable linux partition somewhere, but I sda2,sda5 &sda6 do not have the boot flag?)
/dev/sda6 - 3GB,linux-swap


FYI, there can indeed be a maximum of only 4 primary partitions on a single hard drive. These are numbered from 1 to 4. Primary partitions may be bootable.

An extended partition is a container for logical partitions, as stated before. It's just a container, and cannot hold a filesystem as such; it's also a category of primary partition, hence is also numbered in the 1-4 range.

Should you need more than 4 partitions, you'll use logical partitions; there can be up to 12 of these on a single drive, and they're numbered from 5 to 16. In other words, you can have on a same drive a total of 15 partitions with filesystems : 4 primary (3 with a filesystem + 1 extended) + 12 logical partitions.

Remember you can differentiate primary/logical partitions just from their number. In your particular case, you have : sda1, sda2, sda5 and sda6. Being numbered in the 5-16 range, you know right away that sda5 and sda6 are logical partitions. So you can induce that you have to have an extended partition to hold them : that's sda2; and sda1 is a primary bootable partition.

Please note that the partitions are numbered starting from 1. GRUB starts from 0, so keep in mind that offset if you want to manually edit /boot/grub/menu.lst. Eg: /dev/sda1 is your first partition on your first drive, and GRUB will refer to it as hd(0,0).

Cheers,
Egg

---

