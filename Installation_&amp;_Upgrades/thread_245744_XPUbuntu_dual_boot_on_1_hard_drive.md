---
title: "XP/Ubuntu dual boot on 1 hard drive"
date: 2006-08-28
forum: Installation &amp; Upgrades
---

### Post by andyrobo60 on 2006-08-28
I have just installed ubuntu onto the same hard drive that I was running windows on. The install went fine but after it finnished I reset my pc and when it gets to loading the GRUB boot loader all it says is "Error loading operating system" and stops. Does anyone know how to fix this. Any help will be very appreciated.

---

### Post by jerry_c on 2006-08-28
Dear Andy,

I expect your menu.lst does not match your confirugration. I'd boot from the CD, mount your partitions then run ```
sudo gedit
``` Back up > /boot/grub/menu.lst then edit it.

There's also a grub thread [http://ubuntuforums.org/showthread.php?p=1431959]("http://ubuntuforums.org/showthread.php?p=1431959") with way more info than you'll probably need, since your problem sounds pretty simple.

Good luck.

---

### Post by Fatjoint on 2006-08-28
> **andyrobo60 said:**
> I have just installed ubuntu onto the same hard drive that I was running windows on. The install went fine but after it finnished I reset my pc and when it gets to loading the GRUB boot loader all it says is "Error loading operating system" and stops. Does anyone know how to fix this. Any help will be very appreciated.


If you're seeing "Error loading operating system" I'm going to assume this was Windows that you were trying to boot when you received this error?  
I've run into this a few times when I've installed Linux on a previously installed system with Windows.

Pretty easy to fix and we'll continue if this is the case.

---

### Post by andyrobo60 on 2006-08-28
Ye it looks like ubuntu deleted the windows boot sec and grub didnt take over. i tryed to reinstall the windows boot sec with no luck. so I have deleted all partishions on the drive and am starting over. i hope for better luck this time.

---

### Post by caiman64 on 2006-08-28
I have the same problem... where is the assistance??

Regards,
Carlos

---

### Post by jerry_c on 2006-08-28
Dear Carlos,

I believe Andy's solution of reinstalling everything was like swatting a fly with a sledge hammer, but it seems like all he knew how to do at the time. Check your menu.lst file. It may be a simple as editing it. I doubt you'll need to do a reinstall of any os.

There's a grub thread at [http://ubuntuforums.org/showthread.php?p=1431959]("http://ubuntuforums.org/showthread.php?p=1431959") which might have some relevant info.

I'm a big believer in mounting and just browsing the drives and partitions before doing anything, then backing up the relevant files, like those in /boot, before editing any of them, running grub or anything else that might change what you have. All this can be done from the live CD.

Good luck.

---

### Post by Fatjoint on 2006-08-28
jerry_c,

Unfortunately that seems to be the case most of the time.  With Robo's problem, I'm 99% sure that the only thing needed to be done was to edit the file boot.ini in his windows partition.

---

### Post by 8050 on 2007-03-05
I had the same problem yesterday... The thing is that I don't know how to mount a drive, so I   first I tryed to undo what I did and end up by deleting some part of the boot partition (I think), because when I tryed the partition magic it said that I had a consistency problem with the boot. Now instead of "error in opetating system" I have "Data failure".... Did I mess it for good or can't still try to edit the boot file?

Could you explain how should I mount the drives from the partitioner in the live cd?

Thanks in advance.

Simao

---

### Post by 8050 on 2007-03-05
Nevermind my last post. I just mounted my first drive :-) [http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only](http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only)

---

### Post by Herman on 2007-03-05
[Partitioning Tools ( And which ones not to use )]("http://www.brunolinux.com/04-The_File_System/Partitioning_Tools.html") 

You should make a [Super Grub Disk]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html") before beginning a dual boot install. A SuperGrub DIsk will normally boot Windows easily if the problem is only that your new grub configuration has not automatically set itself up perfectly.

If the problem is in the Windows side of things, which is exceedingly rare, then one of these Windows XP boot floppies is all you need, [How to make your own Windows Xp boot floppy]("http://support.microsoft.com/kb/305595/EN-US/")  
These are much more than just an ordinary boot disk, these have NTLDR, NTdetect, and boot.ini in them. 
Since the floppy is FAT32, you can even edit the boot.ini with different partition numbers if your problem is just that  Windows  has been accidentally allocated a new partition number by a partiton editor. 
It is important to follow the instructions about how to format the floppy disk exactly as specified. 
The once you boot Windows you can make any needed modifications to boot.ini from within Windows itself. This works if you have NTFS or FAT32.
These bypass almost any boot problem you can have and still have a recoverable Windows OS.

If you have FAT32, there is an easier way,  but you need to have relaxed the file permissions beforehand. You can edit your FAT32 boot.ini file directly from Linux, 
[            Mount a Windows FAT32 or NTFS filesystem in the Ubuntu 'Desktop' Live/Install CD]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Windows_with_Dapper_Desktop")

[**            A Birds's eye view of Windows XP **(showing the bootloaderfiles)]("http://users.bigpond.net.au/hermanzone/p6.htm#A_Birdss_eye_view_of_Windows_XP")



Grub does not write to the Windows boot sector, it writes to the hard disk's MBR. 

If you are worried about that, you can back up your bootloader code area of the MBR with the LIveCD, and restore it again whenever you  please, link, [MBR backup and restore]("http://users.bigpond.net.au/hermanzone/p13.htm#mbr_dd")

The hard disk's MBR is not not part of Windows, it is not part of Windows filesystem. 
The MBR is in sector 0 of the hard disk and the rest of the first track is empty and unformatted until sector 63. Often Windows bootsector will be there.

The Windows bootloader lives in the Windows partition and grub lives in the Ubuntu partition. Whichever bootloader's code you write to the boot code area of the MBR will make the MBR point to the bootloader you want.

The command FIXMBR from a Windows  [recovery console]("http://www.kellys-korner-xp.com/win_xp_rec.htm")will make the MBR point to Windows again. 

The FIXBOOT command is for restoring the Windows bootsector if it becomes corrupted somehow. Some people really do make the mistake of installing grub  to Windows bootsector because they read misleading information on the subject and they don't know the difference between a bootsector and a MBR.
Even in the event of that really happening, there is no need to re-install. It can easily be repaired with the FIXBOOT command from a Windows  [recovery console]("http://www.kellys-korner-xp.com/win_xp_rec.htm").

If you have FAT32, it can also be repaired from Linux if you have a type of Windows CD that doesn't have the recovery console.                   [When the bootsector is not the same as its backup]("http://users.bigpond.net.au/hermanzone/p10.htm#differences_between_the_bootsector_and_its_backup")

Dual booting Linux is not at all scary or dangerous when you know what you are doing, 

I hope these tips and tricks will help some people.

Regards, Herman :)

---

### Post by 8050 on 2007-03-05
Well it seems that there is a simple way to it. You don't need to mount anything. You just need to restore the grub and for that matter you just need to follow the instructions

sudo grub install /dev/hda   // hd(x) it can change in our disk so just do a  sudo fdisk -l to see
find /boot/grub/stage1 // it will give you something like (hd0,1). Just use what it will give you
root (hd0,1)
setup (hd0)
quit

And that's it

No more "Error in operating system", no re-install XP! :-)

(Taken from [http://www.guiaubuntupt.org/wiki/index.php?title=Restaurar-Grub](http://www.guiaubuntupt.org/wiki/index.php?title=Restaurar-Grub) (in portuguese))

---

