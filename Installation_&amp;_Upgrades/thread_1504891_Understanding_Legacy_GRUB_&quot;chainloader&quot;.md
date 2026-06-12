---
title: "Understanding Legacy GRUB &quot;chainloader&quot;"
date: 2010-06-08
forum: Installation &amp; Upgrades
---

### Post by holocene on 2010-06-08
The O'Reilly book, Linux in a Nutshell, Sixth Edition has this excerpted section (on Legacy GRUB):

> If GRUB is installed in the MBR, you can chainload Windows by setting the root device to the partition that has the Windows boot loader, making it the active partition, and then using the chainloader command to read the Windows boot sector:

rootnoverify (hd0,0)                  <my comment: indicates a Non-GRUB readable partition, like Windows>
makeactive                                         <my comment: makes partition "active">
chainloader +1                                 <my comment: indicates first sector of current partition>

In this example,...the Windows loader begins at offset 0 of that partition.
If GRUB has been installed to (hd0,0)'s MBR, then I am confused what "file" chainloader +1 is pointing to. Obviously, it is not the MBR but that is confusing to me. 

When one boots a Linux system with GRUB in the MBR, what file does chainloader +1 point to?

A simple clarification would help. 
TIA
Steve.

---

### Post by Herman on 2010-06-08
The Master Boot Record, or MBR for short, is located in sector 0 (zero) of most formatted drives, and is called (hd0) by GRUB.
There is a small amount of space reserved for a little boot loader code in the MBR, plus an ID number for the disk, and the partition table, followed by the bootable disk signature. 

The first sector of a partition can also contain a little bit of code that belongs to a boot loader, and if it does, it may be called a 'boot sector'.
Windows operating systems rely on the boot sector, which contains directions for where to find the boot loader files inside the partition, so the boot sector is kind of like a stepping stone to their boot loader.
Typically, Windows comes installed in primary partition number 1 in most computers when the computer is purchased with Windows already installed in it at the factory. If so the Windows 'boot sector' will be addressed as (hd0,0) by GRUB.

If your computer has more that one disk and you want to chainload the MBR of your second or third disk, you would be chainloading (hd1) or (hd2) and so on, to boot another boot loader if it has code installed in a non-first hard disk's MBR.

If you want to chainload a different partition by the boot sector, (first sector of a partition), you would address it as (hd0,1) or (hd0,2) and so on for partitions in the first hard disk.
For the second hard disk, partitions would be (hd1,0) and (hd1,1) and (hd1,2) and so on ...

Linux operating systems don't rely on having a boot loader code in the first sector of the partition, so if you want to chainload a Linux operating system you either need to install its boot loader to MBR in another hard disk, or install it's boot loader code to the first sector of a partition yourself.
Windows can almost always be chainloaded by a boot sector as long as the boot sector is okay.

SO,
> If GRUB is installed in the MBR, **(hd0)**, you can chainload Windows by setting  the root device to the partition **(hd0,0)**, that has the Windows boot loader,  making it the active partition, **(makeactive)** and then using the chainloader command  to read the Windows boot sector:

rootnoverify (hd0,0) #my comment: indicates a  Non-GRUB readable partition, like Windows# #GRUB doesn't care about booting Windows itself, probably for legal reasons #
makeactive #my comment: makes  partition "active"# #sets the boot flag in case it hasn't already been set#
chainloader +1 #my comment: indicates  first sector of current partition#

In this example,...the Windows loader begins at offset 0 of that  partition.                      

---

### Post by Herman on 2010-06-08
You're not the only one who finds some of these terms confusing. 
Many website authors use the term 'boot sector' loosely to refer to either a MBR or to the first sector of a partition. 
I think it would be fair to say the a MBR can be classed a a special kind of boot sector. If so, the web page author should take a little extra effort to say 'partition boot sector', or 'Master Boot Record' so they're not confusing their readers. 
I imagine that it's more than just laziness, but many web page authors may use pretended laziness to mask the fact that they really don't know enough about their subject.

Another confusing use of terms is centered around the use of the words 'drive' or 'disk'.
A disk is a disk and a partition is a partition, but some web page authors use the words 'disk' or 'drive' when the context implies the author really means to indicate a partition. 
This is going to cause a lot of confusion in the near future when many people start using solid state drives and not just hard disks. 
We used to rely on the word 'hard' before the word 'drive' or 'disk' to indicate we mean an entire hardware object. Now that not all disks are 'hard' ones we'll be limited to the words 'drive' or 'disk' to indicate one entire unit of hardware. :)

---

