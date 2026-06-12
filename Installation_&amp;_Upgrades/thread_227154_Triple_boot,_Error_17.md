---
title: "Triple boot, Error 17"
date: 2006-08-01
forum: Installation &amp; Upgrades
---

### Post by Kuma on 2006-08-01
Hi, I am a bit new to this, but I have been using Ubuntu a few weeks, trying different installations and playing around. This time, i wanted to try a triple boot using ubuntu, windows, and osx86.

I have 4 HDs, three IDE and one SCSI.

hda has osx on it
hdb is fat32 with noting on it
hdd has winxp on it
sda has a fresh install of ubuntu (dapper) on it

Each disk has flawlessly booted at least once during the last day, osx by using the install-cd and removing it as it prompts for input. WinXp by disabling IDE1 in the bios. And ubuntu by using the live-cd to "start from first disk".

:!:  The problem is that the grub bootloader wont work.

Booting ubuntu gives "error 17"
booting xp just doesnt go anywhere
booting osx just reverts back to the grub menu quicker than the eye can see

inserting a live-cd and selecting "boot from first HD" gives the grub menu, and this way i CAN boot Ubuntu but nothing else.

here is all the info I could think of, hope it is enough and not too much :confused: 

--- less etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0 1
/dev/sda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto 0       0




--- sudo fdisk -l

Disk /dev/sda: 18.3 GB, 18373349376 bytes
255 heads, 63 sectors/track, 2233 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2138    17173453+  83  Linux
/dev/sda2            2139        2233      763087+   5  Extended
/dev/sda5            2139        2233      763056   82  Linux swap / Solaris

Disk /dev/hda: 41.1 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        5006    40209088+  af  Unknown

Disk /dev/hdb: 40.9 GB, 40982151168 bytes
255 heads, 63 sectors/track, 4982 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4982    40017883+   c  W95 FAT32 (LBA)

Disk /dev/hdd: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        7297    58613121    7  HPFS/NTFS






--- and finally my menu.lst (commented sections removed)


default		0

timeout		30

title		Ubuntu, kernel 2.6.15-23-386
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd3,0)
kernel		/boot/memtest86+.bin 
boot

title		Other operating systems:
root

title		Microsoft Windows XP Home Edition
map 		(hd0) (hd2)
map 		(hd2) (hd0)
rootnotverify	(hd2,0)
makeactive
chainloader	+1

title 		OSX
rootnotverify	(hd0,0)
makeactive
chainloader 	+1

---

### Post by zxee on 2006-08-01
Some of the comments in menu.lst are used by grub so it would be helpful to see those. I don't know which drive/partition you have grub installed to. Is it on the MBR of your 1st disc?
You may want to try opening a shell when you're booted into ubuntu and doing > sudo grub at the grub prompt> grub > type > find /boot/grub/stage1 grub will respond, hopefully with all the partitions that have a bootable OS.
You can then do > setup (hdX,X) the X's there are just place holders you will need to input the actual drive/partition that you want to install grub to. Hope that helps.

---

### Post by Kuma on 2006-08-01
Thank you for answering! :) 

I seem to have identified at least some part of the problem. The scsi disk is interpreted as hd3 by grub once ubuntu is loaded, but when the computer boots, the scsi disk is hd0, so by changing references to hd3 into hd0 in menu.lst i can now boot into ubuntu.

The command you suggested:
"find /boot/grub/stage1"

lists only (hd3,0) wich RIGHT NOW is the ubuntu disk, but when booting it becomes the osx disk.

disk manager lists each HD as bootable

if i do setup (hdX,X) to the disk of a non-ubuntu OS, wont that screw up that OS:s own bootloader?

---

### Post by zxee on 2006-08-01
> **Kuma said:**
> Thank you for answering! :) 

I seem to have identified at least some part of the problem. The scsi disk is interpreted as hd3 by grub once ubuntu is loaded, but when the computer boots, the scsi disk is hd0, so by changing references to hd3 into hd0 in menu.lst i can now boot into ubuntu.

The command you suggested:
"find /boot/grub/stage1"

lists only (hd3,0) wich RIGHT NOW is the ubuntu disk, but when booting it becomes the osx disk.

disk manager lists each HD as bootable

if i do setup (hdX,X) to the disk of a non-ubuntu OS, wont that screw up that OS:s own bootloader?

To your last question-YES. Don't install grub to a partition that already has a bootloader you want to use. Although if it isn't grub that the OS is loading from it probably wouldn't overwrite anything-still not advisable.

The fact that your drives are playing musical chairs isn't comforting though, and I think you should do some searches on that. I don't have enough experiance with that happening to give you any specific help on that-perhaps it's a bug with the installer? 
I'm reading your post kind of fast. hmm scsi huh. Is your scsi drive from a motherboard port or a pci controller card?
If it's a controller card perhaps that card-the linux support for it is part of the problem.

---

### Post by Kuma on 2006-08-01
musical chairs sums it up nicely...

:!: I have now solved the entire issue, except the mystery of the moving disk. I'm going to look around on that...

The scsi disk is on a PCI-card.

Incidently, the problem only appeared after I installed osx. My working order was this: plug the disks in, winXP installed on its own disk. Install ubuntu, update ubuntu. Booting ubuntu and winXP via grub worked fine. Installed osx, nothing would boot without cd- or bios-tricks. Reinstalled ubuntu, still not working. Switch IDE cables for hda and hdd, made no difference. Changes in menu.lst as above ( worked).

(the osx loader needed to have chainloader +2 for some reason, I discovered by accidental mistyping at the grub commandline..)

---

### Post by Kuma on 2006-08-01
thanks again for taking the time to read my post and answer

---

### Post by zxee on 2006-08-01
Cool! There are no accidents. 
Off Topic: How do you like OS X on X386? I use PPC macs myself.

---

### Post by Kuma on 2006-08-01
Of course, after running the system updates, grub has regenerated the error and completely failed to start again. Insert live-cd, mount sda1, edit menu.lst again. Phew...

Found the error at some bug-report site, seems to be a confirmed ubuntu-related bug rated moderate in importance.

 
And as for the off-topics: OSX - it boots like lightning, faster than anything i have tried. Havent had the chance to try it out beyond that, but I know its a beautiful OS.

---

### Post by zxee on 2006-08-01
> Of course, after running the system updates, grub has regenerated the error and completely failed to start again. Insert live-cd, mount sda1, edit menu.lst again. Phew...

Found the error at some bug-report site, seems to be a confirmed ubuntu-related bug rated moderate in importance.

Darn-that's too bad-are you saying you can't boot into ubuntu again or that after editing menu.lst it now works? 
Just asking for clarification since someone else might find this thread helpful. I wonder if this is a sata issue-although I think you said everything worked until you installed OS X.

---

### Post by zxee on 2006-08-01
> Of course, after running the system updates, grub has regenerated the error and completely failed to start again. Insert live-cd, mount sda1, edit menu.lst again. Phew...

Found the error at some bug-report site, seems to be a confirmed ubuntu-related bug rated moderate in importance.

Darn-that's too bad-are you saying you can't boot into ubuntu again or that after editing menu.lst it now works? 
Just asking for clarification since someone else might find this thread helpful. I wonder if this is a sata issue-although I think you said everything worked until you installed OS X.

---

### Post by Kuma on 2006-08-01
the menu.lst was full of references to the wrong device again, but changing that actually didnt solve the problem, now it just says GRUB and nothing else when i try to boot. :(

the problem appeared around the time when i did install osx, but may also have coincided with some ubuntu update, what i find strange if osx did it, is that osx has its own disk, and afaik it didnt touch any other disk

my disks are just ATA i think? except the scsi one...

---

### Post by amp_man on 2006-08-01
to make it so future kernel updates don't kill your grub config, go into menu.lst with your editer of choice, then search for "groot". This is the grub default root device, as explained in the config file, and any time update-grub is run (such as after an automatic kernel update), grub rebuild the linux potrtion of your menu.lst, using this as the root device. Changing it to your working root (hd0,0)? should fix the problem permanently

edit: sorry, didn't see the second page. When you say it "just says grub", do you mean the normal menu shows up, just with no items in it, or just a simple text on the screen?

---

### Post by Kuma on 2006-08-02
did that groot thing, thanks, saves me a lot of trouble I hope :)

what i meant was this:
the boot sequence simply stated
[INDENT]
Booting from CD: 
GRUB[/INDENT]

the first line is just bios checking for any bootable cd
then it just said GRUB, and froze, presing return killed the screen

fixed it by reinstalling grub from live cd

[INDENT]sudo grub
[INDENT]grub> root (hd3,0)
grub> setup (hd3,0)
[/INDENT][/INDENT]

noting especially that my (hd3) becomes (hd0) when booting
following the instructions found most places and typing
[INDENT]grub> setup (hd0)[/INDENT]
would install over the mbr of my windows drive and break stuff

---

### Post by amp_man on 2006-08-02
well, in all reality, installing grub over your windows mbr wouldn't make a bit of difference. NTLDR is not located in the actual mbr, the mbr contains a pointer to it. Grub emulates this pointer with the chainloader +1 command (at least that's my understanding). so, as long as it was configured correctly, grub would work perfectly fine on your windows drive's mbr. this is how most people configure laptops or computers with just one hard drive, since windows will have to be on the same drive as linux

---

