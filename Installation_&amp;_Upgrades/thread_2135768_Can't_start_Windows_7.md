---
title: "Can't start Windows 7"
date: 2013-04-15
forum: Installation &amp; Upgrades
---

### Post by Noturnoz on 2013-04-15
I've recently installed Ubuntu 12.10 on my pc, but since then I can't load windows. It says "The boot selection failed because a required device is inaccesible." I tried boot-repair nothing changed. Here is my log: [http://paste.ubuntu.com/5710499/](http://paste.ubuntu.com/5710499/) Thanks for help

---

### Post by oldfred on 2013-04-15
Script did not find one of the Windows boot files.
 Vista and win7 boot files
  Boot files/dirs:   /bootmgr /Boot/BCD [COLOR=#ff0000]/Windows/System32/winload.exe
[/COLOR]
Often Windows 7 installs with bootmgr & BCD in a small boot partition that is hidden and winload is in the main install. Or it can be like Vista with all three files in the main install. But you are not showing winload. Script sometimes misses it, so are you able to see that file in your main Windows install?
Since your sda1 is 100MB that is the typical hidden Windows boot partition. And then sda2 is main install?

You also have grldr in sda1? That is grub4dos which often is used by EasyBCD.

You should have a Windows boot loader in sda, and install grub to sdb. Then in BIOS set to boot from sdb as default, but if you have issues you can directly boot Windows from sda. You can also use the one time boot key  - - f12 on my system, but it varies by system.

You also have a boot flag on sdb2. In gpt partitioning you only put a boot flag on the efi partition for booting with UEFI. In MBR(msdos) you put boot flag on the Windows partition with the first two boot files posted above, which you have correctly set on sda1.
Use gparted and remove boot flag from sdb2. But there are a few exceptions. Some Intel motherboard give BIOS boot error is there is no boot flag even with gpt partitioned drives. Only if you get that type of error when directly booting sdb, should you have a boot flag on the gpt drive.

If you can boot Ubuntu do this and choose the drive that is sdb.
      
 sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
The above method of reinstalling will also get grub to remember to reinstall to sdb on major updates. Otherwise it may reinstall to sda.

      
 Restore basic windows boot loader - universe enabled if error on lilo not found
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.

You should be able to directly boot Windows from sda, if Windows is ok. If not then it is a Windows repair issue and you need a Windows repairCD or flash drive.

Once you get Windows working then you can set BIOS to boot from sdb as default and choose Ubuntu or Windows from grub menu.

---

