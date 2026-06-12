---
title: "Boot sector help"
date: 2008-03-29
forum: Installation &amp; Upgrades
---

### Post by graphiteg4 on 2008-03-29
i have recently tried installing  Ubuntu onto an external hard drive but axidently installed the boot sector ont the wrong hard drive. is there any quick fixes or do i have to re install linux again being more care full were  i install the boot sector. any help would be welcomed thanks

---

### Post by LeoSolaris on 2008-03-29
try [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

or [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

One of them might have a tool to help

---

### Post by Herman on 2008-03-29
You shouldn't need to re-install any whole operating system just for the sake of a boot sector.

A boot sector is the first sector of a partition, and for some operating systems, it's a vital steeping stone in the boot process, without which the operating system cannot boot.
Ubuntu and most other Linux operating systems do not have any boot loader code installed in the boot sector (first sector of the partition) by default, but you can install it there if you want to.

The easiest way to install GRUB to the boot sector of your Ubuntu partition is to use [Super Grub Disk]("http://sgd.benjamin-butschko.de/") and make your Super Grub CD, USB or floppy disk.
Once you reboot your PC with Super Grub Disk, go 'Super Grub Disk with Help'--> 'Super Grub Disk'-->'Advanced'-->'GRUB'-->'Restore GRUB in Partition'
OR: 'Super Grub Disk with Help'--> 'Super Grub Disk'-->'Advanced'-->'GRUB'-->'Restore GRUB in Partition (+ Hard Disk)'
You'll be offered choices to select from there regarding which partition and which hard disk you need GRUB restored to.

If you prefer, you can use [GRUB's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli") from either your own copy of GRUB, or from Super Grub Disk, to manually install GRUB anywhere you like, here's one way to do that, [Chainloader Boot]("http://users.bigpond.net.au/hermanzone/p15.htm#Third_method_chainloader_boot").
Or you can use a GRUB Shell from your Ubuntu Live CD to do the same thing, [Re-install GRUB with a GRUB shell]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD").

---

### Post by Herman on 2008-03-29
:) 
IF on the other hand, you mean you install GRUB to MBR in the wrong hard drive's MBR, you can also use Super Grub DIsk to fix your problem.

A MBR (short for Master Boot Record), is found on every formatted hard disk.
The MBR of a hard disk is quite distinct from a mere boot sector of a partition. 
While a hard disk's MBR is technically a special kind of boot sector, it is does not belong to any operating system's partition or file system, and in fact contains the hard disk's partition table itself. 
There can only be one Master Boot Record per hard disk, but there can be as many partition boot sectors as there is partitions.

Super Grub Disk can install GRUB to any MBR you like if you have more than one hard disk, it makes no difference whether you have USB hard disks or internal ones.
Once you reboot your PC with Super Grub Disk, go 'Super Grub Disk with Help'--> 'English Super Grub Disk'-->'Advanced'-->'GRUB'-->'Gnu/Linux (Advnaced)'-->'Fix Boot of Gnu/Linux (GRUB)'-->'Manual Restore GRUB in Hard Disk (MBR)'-->'Manual Restore GRUB in Hard Disk (MBR)'-->'Partition of GRUB'-->(And select your Linux Partition),--> 'Restore to MBR of Hard Disk', (and select whichever hard disk you want to install GRUB to MBR in from the list provided). Then reboot and eject your Super Grub Disk CD.

Or, you can use [GRUB's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli") from either your own copy of GRUB, or from Super Grub Disk, to manually install GRUB any hard disk you like.
Or you can use a GRUB Shell from your Ubuntu Live CD, [Re-install GRUB with a GRUB shell]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD").

---

### Post by Herman on 2008-03-29
:)
If you installed GRUB or any other boot loader by mistake to the wrong hard disk (MBR), you can replace GRUB again with a different boot loader of your choice simply by overwriting GRUB's code in whichever hard disk's MBR it is with whatever boot loader or boot manager's code you like. 
Normally whatever boot manager you had in it before.
For Windows 95, 98 and ME, you need the right floppy disk for your particular version of Windows, I like the ones from [bootdisc.com]("http://www.bootdisk.com/") best.
When you boot your PC up with  a boot floppy disk, you use the command: fdisk /mbr to restore Windows code in your first hard disk's MBR. 
Illustrated link: [Windows 98 Floppy Disk Method]("http://www.users.bigpond.net.au/hermanzone/p18.htm#Windows_98_Floppy_Disk_Method")...also works for XP even if your dog ate your 'Install' CD

If you have Windows XP, you would use your Windows XP 'Recovery Console'
              Just put in your Windows XP install CD, and boot into the [recovery console]("http://www.kellys-korner-xp.com/win_xp_rec.htm") and use the so-called 'FIXMBR' command.
The Windows recovery console's FIXMBR command is, as the name implies, for the MBR  (of the first hard disk).
Whether you think it 'fixes' anything or not depends on your point of view, if you're a Windows user you might think it 'fixes' your MBR. GRUB users might not share your taste in boot managers though. :)

On the other hand, if you  installed a boot loader to an operating system's boot sector which wasn't designed or intended to have that particular boot loader code installed in it, it wouldn't do that operating system any good and would probably prevent it from booting. 
It's generally good to install GRUB to MBR in most hard disks, but it might be bad to install GRUB to a non-linux boot sector.
If it's just the first sector of a data partition or even an extended partition, it's okay to install GRUB there. But GRUB might not be good to a foreign operating system.

If you wanted to restore your Windows 95, 98 or ME   boot sector, you would use quite a different command, because a boot sector is not the same thing as a MBR.
The command for fixing a Windows boot sector is: SYS C: and you can run that from your Windows 95 or 98 or ME boot floppy disc to restore the boot sector and IO.SYS and other important files to do with booting.

If you want to install Windows XP boot loader code in the boot sector, you would use the FIXBOOT command instead. 
That will fix your Windows XP boot sector, (without a doubt).

This is because a boot sector and a MBR are two different things.

For some reason, there is widespread confusion about boot sectors and MBRs, and it is often the fault of authors of web sites who often use the terms interchangeably, and even makers of computer parts and people who write CMOS programs, and some kinds of software. One would expect those people to know best.  No wonder every one else finds these terms confusing too.



:) Regards, Herman

---

