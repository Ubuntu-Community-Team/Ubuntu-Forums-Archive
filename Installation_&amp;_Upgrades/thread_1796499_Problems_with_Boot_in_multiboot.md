---
title: "Problems with Boot in multiboot"
date: 2011-07-03
forum: Installation &amp; Upgrades
---

### Post by jcleaver42 on 2011-07-03
I am having an issue that I caused myself.  I had Win 7 and decided to install Ubuntu.  I set up a dual boot and all was well.  I had a Win7 system that worked well, and an Ubuntu system set up the way I wanted.

Then, I had a wild hair.  I decided I wanted a WinXP system as well to run some older programs that won't work in Win7.  So i followed the steps I found to set up Win 7 and WinXP.  In the instructions, they had me load and configure EasyBCD; which claims you can set up a Linux boot.  

So, now I have a Win 7 and Win XP dual boot; but I can't seem to figure out how to get Ubuntu listed and to actually boot.  I did try to use Neogrub, but my configuration must be incorrect.  I installed Ubuntu to the second Hard drive, and to the second partion.  It is now an ext3 partition.  The third partition is a Linux Swap.  When i configured NeoGrub to boot to hd1,1, it says it isn't a bootable disk.

Any help would be appreciated.

John

---

### Post by drs305 on 2011-07-03
It would be helpful for us to see the status of your boot files. This can be done by downloading/extracting and running the boot info script and posting the contents of the file it generates: RESULTS.txt.

Boot the LiveCD, then click on the BIS link in my signature line or go to [http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net") to download the script and get instructions.

If your Windows bootloader is only on your first drive, you can always install Grub2 on the second drive (not the partition). It may pick up Windows, but if not you could always change the BIOS to boot the second drive first to get into Ubuntu (until you get things set up correctly). We can tell you how to do it if you wish, leaving sda (Windows) untouched.

---

### Post by jcleaver42 on 2011-07-04
Attached is my results.txt file.  

It does include what i tried for the neogrub configuration for EasyBCE.

Sorry it took so long, it took me a while to figure out the syntax from the LiveCD.

[ATTACH]196654[/ATTACH]

---

### Post by oldfred on 2011-07-04
It looks like you should just be able to install grub2's bootloader to the MBR of sdb and set BIOS to boot sdb and it should work.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sdb5 and want grub2's bootloader in drive sdb's MBR:
#Find linux partition, change sdb5 if not correct:
sudo fdisk -l
#confirm that linux is sdb5
sudo mount /dev/sdb5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdb
#If grub 1.99 with Natty uses boot not root
sudo grub-install --boot-directory=/mnt/ /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sdb
# If no errors on previous commands reboot into working system and run this:
sudo update-grub

Check that grub will reinstall to your sdb drive. It should also show serial number or something that makes sdb different than sda.

#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

---

