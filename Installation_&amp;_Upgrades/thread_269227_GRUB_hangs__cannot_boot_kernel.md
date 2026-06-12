---
title: "GRUB hangs / cannot boot kernel"
date: 2006-10-01
forum: Installation &amp; Upgrades
---

### Post by willyzzzz on 2006-10-01
Hi all,

after installing Ubuntu 6.06.1 LTS (Dapper Drake) Desktop via the Live-CD's desktop link, GRUB is unable to boot the kernel from HDD. I browsed both forums and GRUB documentation, but  I was not able find a solution (probably it lies in front of me). I compiled a short abstract of what I did with remarkable (to me) items. I hope that this is more convenient for you than describing it in full prose.

Thanks for help!
Cheers,
Willy

[LIST=1]

[*]Prerequisite

[LIST]
	[*]Before installing Ubuntu I had Windows 2000 alone on the PC (no dual boot loader)
	[*]Win2k booted from HDD with no problems
[/LIST]

[*]Installation

[LIST]
	[*]Manual partitioning to use entire disk space (see fdisk output below)
[/LIST]

[*]Booting from HDD

[LIST]
	[*]GRUB says:[INDENT][FONT="Courier New"]GRUB Loading stage1.5...
	GRUB loading, please wait...
	[*GRUB hangs, HDD-LED permanent-on*][/FONT][/INDENT]
	
[/LIST]

[*]Booting Live-CD again

[LIST]
	[*]mounting and using /dev/hda1 is possible
	[*]fdisk -l says:[INDENT][FONT="Courier New"]Disk /dev/hda: 6400 MB, 6400235520 bytes
	255 heads, 63 sectors/track, 778 cylinders
	Units = cylinders of 16065 * 512 = 8225280 bytes
		
	Device Boot      Start         End      Blocks   Id  System
		/dev/hda1   *           1         742     5960083+  83  Linux
		/dev/hda2             743         778      289170    5  Extended
		/dev/hda5             743         778      289138+  82  Linux swap / Solaris
	
	Partition 1 has different physical/logical endings:
     phys=(945, 49, 63) logical=(160, 35, 63)

	[/FONT][/INDENT]
	[*]Create boot floppy disk
	[LIST]
		[*]followed descripton of [GrubHowto/BootFloppy]("https://help.ubuntu.com/community/GrubHowto/BootFloppy")
		[*]step 3: used /boot/grub/* from HDD
		[*]step 4: GRUB says:[INDENT][FONT="Courier New"]grub> root (fd0) Unknown partition table signature
 Filesystem type is ext2fs, using whole disk[/FONT][/INDENT]
 	[/LIST]
	
[/LIST]

[*]Booting from floppy

[LIST]
	[*]GRUB says:[INDENT][FONT="Courier New"]GRUB Loading stage2.......
	Press ESC to enter the menu...
	[*timeout*]
	Booting Ubuntu, kernel 2.6.15-26-386'
	root (hd0,0)
	Filesystem type is ext2fs, partition type 0x83
	kernel /boot/vmlinuz-2.6-16-26-386 root=/dev/hda1 ro single
	[*GRUB hangs, HDD-LED permanent-on*][/FONT][/INDENT]
	
[/LIST]

[/LIST]

---

### Post by Herman on 2006-10-01
After BIOS POST the following white printing appears on your black monitor background,

>                     grub loading stage1_5
 grub loading...please wait                And grub nothing more happens, it stays like that.
 
f this happens to you (especially after a new install, or an update), it could be caused by corruption in  stage1_5  or  stage2  files in your /boot/grub directory.
 These files can easily be removed and replaced with fresh new files in a few minutes if you can type the right commands. 
 
 Boot the system up with Super Grub Disk (Better use the 'direct boot' option as this bypasses the use of those corrupt files for booting with).
 Then open a terminal and type the following commands,
```
sudo cp /boot/grub/menu.lst .
  sudo rm /boot/grub/*
  sudo cp menu.lst /boot/grub/
  sudo grub-install /dev/hda
```If that doesn't work, (but I think it will if the rest of our install is okay, (did you check your CD for defects before your began your install?)

Get a [Super Grub Disk]("http://adrian15.raulete.net/grub/tiki-index.php"), you can boot with that for the time being. You can use Super Grub Disk's stage2 eltorito, if you can't get access to your own Grub files, or you Grub is still corrupt.

When you feel like it, sometime when you are booting, rather than booting up by the menus, press 'c' to get into Super Grub's [Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli")
(other versions of Grub have that too). 
Use the Command Line to investigate your computer, 
How to get GRUB's Command Line to investigate a computer.........................................[GO]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_get_GRUBs_Command_Line_to_investigate_a_computer")

Boot Ubuntu up with the information you find out from the CLI mode Grub, taking notes while you are doing it. You can edit your menu.lst with the same information.
You can diagnose and solve a lot of problems using CLI mode Grub because it provides more feedback.

Regards, Herman :D

---

### Post by raphha on 2006-10-01
well...

I don't really see what's going on, but what trying to reinstall grub from the live-cd...?

You could try (in a shell under the live system)
[LIST]
[*] mount /dev/hda1 /mnt
[*]chroot /mnt /bin/bash
[*]grub-install /dev/hda
[/LIST]

Check the /boot/grub/menu.lst first if you can see anything strange in there...

raph

---

### Post by willyzzzz on 2006-10-02
Hi Herman,
Hi raphha,

thanks for your answer.

Herman wrote:
> did you check your CD for defects before your began your install?)

Yes, I did.

Since the [Suber Grub Site]("http://adrian15.raulete.net/grub/tiki-index.php") seems to be unavailable at present I was not able to try the rest, so I tried raphha's idea.

Additionally to what raphha proposed I had to obtain root priviledge using  *sudo -s*, so the full command sequence was:

```

[FONT="Courier New"]
ubuntu@ubuntu:~$ sudo -s
root@ubuntu:~# mount /dev/hda1 /mnt
root@ubuntu:~# chroot /mnt /bin/bash
root@ubuntu:~# grub-install /dev/hda
/dev/hda: Not found or not a block device
[/FONT]

```

As you can see the grub-install failed. I cross-checked with the "Disk Manger" from the Menu "System" > "Administration" and that one reports the HDD as present and on the "Partitions"-tab partion 1 /dev/hda1 as being mounted to "Access Path" /mnt. So everything should be ok with the HDD and its partions, right?

Cheers,
Willy

---

### Post by raphha on 2006-10-02
Maybe the boot sector is corrupt? You could try to install grub on a floppy (the boot directory can stay on hda, just the grub-install goes to the floppy instead of the MBA. If this works, your HD's MBA might be the problem.

On way to "clean" the boot sector is to use "dd" to copy zeros form /dev/zero to the first 512 bytes of your disk (as root):
"dd if=/dev/zero of=/dev/hda count=1 bs=512". Maybe this helps? (Then reinstall grub)

raph

---

