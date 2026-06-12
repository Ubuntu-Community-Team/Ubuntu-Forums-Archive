---
title: "filesystem for SSD question"
date: 2008-09-02
forum: Installation &amp; Upgrades
---

### Post by chavli on 2008-09-02
I just recently bought a solid state drive for my laptop and I'm about to install Ubuntu on it. But before I do that, is there a filesystem that is optimized for SSD's?

---

### Post by dicecca112 on 2008-09-04
none, but its been said that ext2 or ext3 tweaked is better, normal ext3 is thought to kill drives faster, its not been proven though

---

### Post by Herman on 2008-09-12
Check whether or not your SSD features a controller for 'wear levelling' and 'error correction'.
If it does, then you don't need any special file system because you'll be writing to the flash memory's controller and not to directly to the raw disk. 
The flash memory controller provides a fake layer between the operating system and the raw disk. It makes the flash memory appear to the operating system and the user as a hard disk. 
Meanwhile, behind the scenes, the controller will be busy shuffling the flash memory's blocks around and rotating your files and data so you don't keep wearing out any one particular block. (The file system's journal blocks in particular). That way your flash memory will last for many years, much longer than a hard disk probably, regardless of what file system you think you're using (on the 'surface').

This whole page, [Flash memory]("http://en.wikipedia.org/wiki/Flash_memory") from Wikipedia has good information, 
particularly this part, Quoted from [Flash memory]("http://en.wikipedia.org/wiki/Flash_memory") - WikiPedia: 
> **Flash file systems** 
**Because of the particular characteristics of flash memory, it is best used with either a controller to perform [wear-levelling]("http://en.wikipedia.org/wiki/Wear-levelling") and [error correction]("http://en.wikipedia.org/wiki/Error_correction")** or specifically designed [file systems]("http://en.wikipedia.org/wiki/File_system") which spread writes over the media and deal with the long erase times of NOR flash blocks. 
The basic concept behind flash file systems is: When the flash store is to be updated, the file system will write a new copy of the changed data over to a fresh block, remap the file pointers, then erase the old block later when it has time. One of the earliest flash file systems was [Microsoft]("http://en.wikipedia.org/wiki/Microsoft")'s FFS2 (presumably preceded by FFS1), for use with [MS-DOS]("http://en.wikipedia.org/wiki/MS-DOS") in the early 1990s.[[12]]("http://en.wikipedia.org/wiki/Flash_memory#cite_note-11")
 Around 1994, the [PCMCIA]("http://en.wikipedia.org/wiki/PCMCIA"), an industry group, approved the **Flash Translation Layer (FTL)** specification, which allowed a [Linear Flash]("http://en.wikipedia.org/wiki/Linear_Flash") device to look like a [FAT]("http://en.wikipedia.org/wiki/File_Allocation_Table") disk, but still have effective [wear levelling]("http://en.wikipedia.org/wiki/Wear_levelling"). Other commercial systems such as FlashFX and FlashFX Pro by Datalight were created to avoid patent concerns with FTL.
 [ZFS]("http://en.wikipedia.org/wiki/ZFS") by [Sun Microsystems]("http://en.wikipedia.org/wiki/Sun_Microsystems") has been optimized to manage Flash SSD systems, both as cache as well as main storage facilities, available for [OpenSolaris]("http://en.wikipedia.org/wiki/OpenSolaris"), [FreeBSD]("http://en.wikipedia.org/wiki/FreeBSD"), and [Mac OS X]("http://en.wikipedia.org/wiki/Mac_OS_X") operating systems. Sun has announced a complete line of Flash enabled systems and storage devices.
 [JFFS]("http://en.wikipedia.org/wiki/JFFS") was the first flash-specific file system for [Linux]("http://en.wikipedia.org/wiki/Linux"), but it was quickly superseded by [JFFS2]("http://en.wikipedia.org/wiki/JFFS2"), originally developed for NOR flash. Then [YAFFS]("http://en.wikipedia.org/wiki/YAFFS") was released in 2002, dealing specifically with NAND flash, and [JFFS2]("http://en.wikipedia.org/wiki/JFFS2") was updated to support NAND flash too.
 **In practice, flash file systems are only used for "[Memory Technology Devices]("http://en.wikipedia.org/wiki/Memory_Technology_Device")" ("MTD"), which are embedded flash memories that do not have a controller. **[B]
Removable flash [memory cards]("http://en.wikipedia.org/wiki/Memory_card") and [USB flash drives]("http://en.wikipedia.org/wiki/USB_flash_drive") have built-in controllers to perform [wear-levelling]("http://en.wikipedia.org/wiki/Wear-levelling")[error correction]("http://en.wikipedia.org/wiki/Error_correction") so use of a specific flash file system does not add any benefit. 
[/B] These removable flash memory devices use the [FAT]("http://en.wikipedia.org/wiki/File_Allocation_Table") file system to allow universal compatibility with computers, cameras, PDAs and other portable devices with memory card slots or ports.
In some (but not all) USB flash memory sticks, the reiserfs file system seems to give a significant speed advantage compared with any other file system. I don't know why but I guess maybe it works better with some flash memory controllers. In other flash memories it doesn't seem to give as much improvement over ext3.
We can use a program called bonnie++, (installable in Ubuntu), to test the speed of various drives and file systems.
I'm using reiserfs for my flash memory devices.  :)

---

### Post by chavli on 2008-09-16
thanks for the info herman, helped alot:)

---

### Post by FrankVdb on 2008-09-22
The quoted information clearly refers to removable flash drives. There could be major differences with solid state *drives*.

---

