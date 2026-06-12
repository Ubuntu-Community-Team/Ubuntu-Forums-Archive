---
title: "USB drive install went wrong. Need help fixing Grub."
date: 2011-03-05
forum: Installation &amp; Upgrades
---

### Post by gearheaded on 2011-03-05
I installed Ubuntu 10.10 on a USB drive recently. My problem is that Ubuntu also went ahead and installed it's bootloader on my primary hard drive without asking me to! :( On Ubuntu 10.04 it gives you an option of where to install the bootloader, but now Ubuntu just installs it automatically without asking. So I have a number of problems I need to fix now:

1. This one is probably easy: how do I change my default boot options so that the computer will boot into Windows by default instead of Ubuntu?

2. How can I put a copy of the Grub bootloader on the USB drive so it is bootable on other computers?

3. How can I get the Windows 7 bootloader properly reinstalled on the main hard drive so I have access to normal Windows boot options like safe mode?

4. I can't boot into my system at all now without the USB drive connected now. Grub seems to look for the USB drive, and when it does not find it, it gives me an error and sends me a grub commandline that I don't understand.

So how can I tell Grub to not crash when it can't find the USB drive and just give me the option to boot into Windows again?

I tried editing /etc/default/grub according to this guide [http://www.nixiepixel.com/grub2-bootloader/](http://www.nixiepixel.com/grub2-bootloader/) but I didn't find any useful options. I'm sort of used to Grub 1, but Grub 2 has me confused. Any help is greatly appreciated!

---

### Post by tlcstat on 2011-03-05
Greetings,
In the future, disconnect your HD before installing to usb drive. I did this myself once, could only boot HD from USB. This fixed it. Bit techie but that our Linux!

This is a cut and past from a Grub support page.

**[COLOR=Navy][SIZE=3]Reinstalling GRUB 2 from LiveCD[/SIZE][/COLOR] **
If you cannot boot from GRUB 2 and need to reinstall it, here is the simple method. For more details or for advanced options, refer to the Ubuntu community documentation here: [Grub2 - Reinstalling GRUB 2]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202"):
[LIST]
[*]Boot the Ubuntu Live CD (Try without installing).
[*]From the Desktop, open a terminal - Applications, Accessories, Terminal.
[*]Determine your normal system partition - `sudo fdisk -l` (That is a lowercase L)
[*]If you aren't sure, run `df -Th`. Look for the correct disk size and ext3 or ext4 format.
[*]Mount your normal system partition: Code:
sudo mount /dev/sdXY /mnt 

[LIST]
[*]If you aren't sure if you mounted the correct partition, once it's mounted run "nautilus /mnt" to inspect the partition. If it is the correct partition, you should see the normal Ubuntu folders such as /bin, /boot, /etc, /home, etc
[/LIST]

[LIST]
[*]Example: sudo mount /dev/sd*a1* /mnt
[*]Note: The partition to mount is normally the partition on which Ubuntu was installed: sda1, sdb5, etc. If you have a separate /boot partition, use the device on which the /boot partition is located. Grub 2 works best when installed in the MBR of the drive to which BIOS boots. Also remember that you *mount* the partition (including the number) in this step, but you do *not* include the partition number when you run the "sudo grub-install" command later.
[*]Note: GRUB 2 counts the first drive (X) as "0", but the first partition (Y) as "1"
[/LIST]
[*]Only if you have a separate boot partition:
[LIST]
[*] Code:
sudo mount /dev/sdXY /mnt/boot 
with sdXY being your /boot partition designation.
[/LIST]
[*]Reinstall GRUB 2: Code:
sudo grub-install --root-directory=/mnt /dev/sdX 
Do NOT include the partition number.
[*]
[LIST]
[*]Example: sudo grub-install --root-directory=/mnt /dev/sd*a*
[*]Note: Substitute the device on which Ubuntu was installed - sda, sdb, etc. Do *not* specify a partition number.
[/LIST]
[*]Unmount the partition *: Code:
sudo umount /mnt 

[LIST]
[*]* Note: If you mounted a separate /boot partition, unmount it first: 
Code:
sudo umount /mnt/boot 
[/LIST]
[*]Reboot.
[/LIST]

---

### Post by oldfred on 2011-03-05
If you can boot into Ubuntu you can just reinstall grub to any drive from the working install. 

#reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub
#to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

You can use windows tools to fixMBR or install this which works just as well from Ubuntu.
Restore basic windows boot loader - universe enabled
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

---

