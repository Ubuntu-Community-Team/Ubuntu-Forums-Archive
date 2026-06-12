---
title: "grub 'no such device' with dual disk GPT/mbr setup"
date: 2016-06-13
forum: Installation &amp; Upgrades
---

### Post by boolewinklegmail. on 2016-06-13
Hello,


Background, I have a 2008 era bios-based machine that I want to upgrade/replace. It has a 500g drive.
I have just installed a 4TB disk, and am trying to install a more modern 64bit ubuntu on this disk.
Although grub has been installed on the new disk (about 10 times!), booting from the new disk
seems to actually boot from the old disk. More details:


The old disk (sda) has MBR partitioning, 4 partitions (one is windows).
The new disk (sdb) is setup with GPT partitioning, including
[INDENT][FONT=courier new]1M    bios_grub[/FONT]
[FONT=courier new]300M    fat32        # not used/efi boot flag not set, reserved for future use (ambition to put the drive in a [/FONT][FONT=courier new]uefi[/FONT][FONT=courier new] machine)[/FONT]
[FONT=courier new]20g    ext4 / # gpt partion 3, /boot is here[/FONT]
[FONT=courier new]15g     swap[/FONT]
[FONT=courier new]3TB    /home[/FONT][/INDENT]


So, I have repeatedly done (when booted into the 64bit linux, and from a rescue disk)
[INDENT][FONT=courier new] sudo grub-install /dev/sdb[/FONT]
[FONT=courier new] sudo update-grub[/FONT][/INDENT]


During the original install, I forgot to point it at /dev/sdb, 
so booting /dev/sda now has an option to boot the new system as well as the old. It works.
However, I want to move away from dependence on the old drive, and just boot from the new.


When I boot from the new drive, it always gives[INDENT][FONT=courier new]error: no such device: 4a096....[/FONT][/INDENT]
[INDENT][FONT=courier new]grub rescue> [/FONT][/INDENT]


Following a lot of web surfing, I got tho this bit of evidence:[INDENT][FONT=courier new]grub rescue> set[/FONT][/INDENT]
[INDENT][FONT=courier new]grub rescue> ls[/FONT][/INDENT]
[INDENT][FONT=courier new](hd0) (hd1) ... (hd1,gpt3) ...[/FONT][/INDENT]
[INDENT][FONT=courier new]prefix=(hd0,1)/grub[/FONT][/INDENT]
[INDENT][FONT=courier new]root=hd0,1[/FONT][/INDENT]
Here, (hd1,gpt3) is the newgpt partition that has /boot. (... means other irrelevant partitions).


However, I understand (correct?) that the root=hd0,1 is reporting that grub actually booted from the old drive,
EVEN THOUGH 
1) I told it to boot from the new drive in the bios,
2) I know that the bios order has an effect because booting from the other drive actually works.
(As well, in a previous life of this upgrade drama, I was booting from the new drive successfully).


From the grub rescue menu, these commands successfully boot the new linux:[INDENT][FONT=courier new]set prefix=(hd1,gpt3)/boot/grub[/FONT][/INDENT]
[INDENT][FONT=courier new]set root=(hd1,gpt3)[/FONT][/INDENT]
[INDENT][FONT=courier new]insmod[/FONT][FONT=courier new] normal[/FONT][/INDENT]
[INDENT][FONT=courier new]normal [/FONT][/INDENT]



*So it seems like grub is initially looking at the **gpt** disk, then giving up and redirecting itself **back to the **mbr** disk?* 

Another puzzle is that the "no such device" UUID 4a09... 
is not one of the partitions on either disk - it is not in the output of "sudo blkid",
which shows all the partitions on both disks. Nor does this string "4a09..." appear
in the grub.cfg file on either drive.


I am a programmer, but not a linux or hardware expert, please keep your reply (if any) on the simple side!

---

### Post by oldfred on 2016-06-13
Grub could be confused, but since it boots by UUID it still should work.

With multiple drives, your boot drive in BIOS is always hd0 in BIOS/grub.
I used to boot from sdc, then with another drive sdd. But had skipped a port on SATA port order. So flash drive was sde whne plugged in, but on reboot flash drive was sdb. I had skipped SATA1. System still booted ok, but I had some manual boot commands to boot ISO directly and often had to manually edit them as drive order changed.

        
 May be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

You mention you installed to drive that is now sda, best to update your install to have correct drive.
Grub remembers drive it installs into and on a major update will reinstall to that drive.

       
 #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc # for BIOS with grub-pc 
It will show drive model & serial number
to see similar drive info
sudo lshw -C Disk -short  
    sudo grub-probe -t device /boot/grub 
   #to get grub2 to remember where to reinstall on major updates
sudo dpkg-reconfigure grub-pc 
#Enter thru first pages,tab to ok, spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

---

### Post by Dennis N on 2016-06-13
> During the original install, I forgot to point it at /dev/sdb,
so booting /dev/sda now has an option to boot the new system as well as the old. It works.

I assume this refers to the install on sdb? If this was never fixed, then even when you set sda as the 1st boot drive, you would actually boot into the grub menu of the OS installed on sdb (since you installed its grub to the MBR of the old disk sda - the MBR on sda directs the boot process to continue booting on sdb).

Fix this by booting to the OS on sda, then in it's terminal:

```
sudo grub-install /dev/sda
sudo update-grub
```

P.S. I've never mixed disks types like you have done: gpt and ms-dos partitioning, but I don't think that is a factor.

---

### Post by Dennis N on 2016-06-13
```
Another puzzle is that the "no such device" UUID 4a09...
is not one of the partitions on either disk - it is not in the output of "sudo blkid"
```

It may have been there at one time. Did you delete any partitions?

Case in point: Once I deleted and recreated a swap partition. This changed the UUID of swap, and the boot process hung waiting for the old partition to be ready. Fixed by changing the UUID in /etc/fstab.

---

### Post by boolewinklegmail. on 2016-06-15
Hello,  thank you for the help.

Running the repair option of the BootRepar disk fixed it.  

I now think it was because the original ubuntu installer/live disk usb was still in the machine when
grub-install was run, and grub found this usb disk as well as the two hard drives.
So (speculating) the 'no such device' was actually the usb disk.

---

