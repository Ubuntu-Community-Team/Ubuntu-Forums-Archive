---
title: "Another option for multi-boot - Grub for DOS"
date: 2007-02-21
forum: Installation &amp; Upgrades
---

### Post by mike_f on 2007-02-21
[FONT="Courier New"]
Like many fellow posters, I've suffered much multi-boot pain over the years. Since a Ubuntu installation invariably brings along GRUB, I successfully migrated my simple 'boot manager' partition to FreeDOS and GRUB for DOS. This strategy implements a GRUB setup that (IMHO) is easier to recover than Linux or Windows.

A condensed description of GRUB follows. GRUB installations consist of three parts called stages. Stage 1 is usually installed in the hard disk Master Boot Record and points to the partition where the following stages reside. Stage 1.5 is the code that allows GRUB to read the partitions specific file system e.g. ext3, FAT32. Stage 2 is the GRUB 'interpreter' that reads menu.lst, displays the selection menu and, optionally, performs other GRUB directives. For further info, visit [http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html).

For now, I'll list the major steps to install FreeDOS and GRUB for DOS. If I don't get flamed too badly :) I'll add more detail as requested.

- WARNING - this procedure will change the primary partition layout - existing installations of Windows and Linux probably won't boot. Changes to boot.ini and /etc/fstab respectively are required and can be accomplished using a rescue CD of your choice (my recommendations below). 

- First, download a FreeDOS CD image from freedos.org and burn it.
- If needed, download a GPARTED LiveCD image from gparted.sourceforge.net and burn it. Alternatively, you could use a commercial partition resizer like Symantec Partition Magic or Acronis Disk Director. There are issues with using Partition Magic, more on that later.
- Download Grub4DOS from sarovar.org and copy to your media of choice.
- Using your partition resizer, create a 500 Mb partition at the beginning of your first hard disk. My preferred layout is: 
primary partition 1 - 500 MB - FreeDOS
primary partition 2 - 4 GB - Windows
primary partition 3 - 4 GB - Ubuntu 
extended partition with
logical partition 1 - remaining space - Shared data - FAT32 
logical partition 2 - 500 MB - Linux swap
NOTE - the extended partition for shared data could be a larger, second hard disk or even a NAS, leaving the last (fourth) partition for Linux swap.
NOTE - multiple copies of Windows and DOS should each have their own primary partition so they are hidden from each other and will stay 'drive C'.
WARNING - Partition Magic is very picky about disk geometry settings in partition records, so use of non-PM resizers will probably prevent you from using PM on the hard disk again!

- reboot from the FreeDOS CD and install FreeDOS on the first partition. Only a minimal installation is needed which should take far less than 500 MB. 
- unzip grub4dos into its own directory on the C drive.
- copy GRLDR from the grub directory to the root directory.
- create a simple Grub config (menu) file named MENU.LST in the root directory which would look something like:

# ----- menu.lst - see grub documentation and original menu.lst
## default - num or saved (savedefault entry)
default		0
## fallback - if boot fails, fall back to alternate menu entry
fallback 		1 	
## timeout sec
timeout		10

# entry 1
title			Free-DOS - partition 1
hide 			(hd0,1)
unhide 		(hd0,0)
root			(hd0,0)
makeactive
chainloader	+1
boot

# entry 2
title			Windows - partition 2
hide 			(hd0,0)
unhide 		(hd0,1)
root			(hd0,1)
makeactive
chainloader	+1
boot

# entry 3
title			Ubuntu - partition 3
root			(hd0,2)
kernel		/boot/vmlinuz root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img 
quiet
boot
# ---------------- end of menu.lst ---------------
NOTE - Grub numbers hard drives and partitions starting with zero.

- Use the bootlace program that comes with GRUB4DOS to write GRUB to the Master Boot Record (MBR). Note that this is different than other Grub installs which use Setup.
- Reboot and make sure that the GRUB4DOS menu appears.  
- If you have an existing Windows partition, reboot with a DOS based rescue CD (I use FreeDOS). If necessary, make the Windows partition active and reboot again:\. Edit boot.ini and change the partition number as appropriate.
- If you have an existing Linux partition, reboot with a Linux based rescue CD (I recommend Trinity Rescue Kit), mount the partition, edit /etc/fstab and change the partition devices as appropriate.
- New installations of Windows and Linux after the above procedure will overwrite the MBR, so you will have to reactivate the DOS partition and rerun bootlace to restore your GRUB For DOS menu.
-Whew!
 
[/FONT]

---

