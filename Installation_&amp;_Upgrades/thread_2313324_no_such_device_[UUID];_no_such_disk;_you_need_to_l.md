---
title: "no such device [UUID]; no such disk; you need to load the kernel first"
date: 2016-02-11
forum: Installation &amp; Upgrades
---

### Post by two4two on 2016-02-11
Ubuntu Studio 14.04.03 LTS 32-bit.  I have THREE hard drives.  Two of them are PATA, 250GB each, and have been there for several years.  I recently added a 1TB SATA 150 drive.  I used GPARTED from a live Ubuntu Studio 14.04 DVD to define it as an MBR disk and created 4 primary partitions: 1=85GB EXT4 to install Ubuntu Studio 14.04, 2=85GB NTFS for future OS, 3=85GB NTFS for future OS, and 4 = the remainder of the TB (850GB??) NTFS for data.  My Windows XP and existing Ubuntu 11.04 (on HD1) recognize all 4 partitions on this drive.

On one of the hard drives, first partition, I have Win98SE which I actually don't use, but it has the boot.ini for my multi-boot.  It also has a little piece of software called BOOTPART which I use to get the 512-byte boot sector bootloader and add to the boot.ini.

On the next hard drive on the first partition is WinXP.  As I said earlier the boot.ini on the first drive controls booting to this.  On the second partition of this hard drive is Ubuntu Studio 11.04.

So I inserted my Ubuntu Studio 14.04.03 live DVD and executed "install Ubuntu......".  I chose the option to manually decide where/how to install and I chose the first partition on the 1TB SATA drive (as mentioned earlier, already defined as EXT4). I specified it would be mounted to "/".  And I specified that the boot loader would be installed in this partition (not to the MBR or anywhere else) so that I could use my little BOOTPART software to get the 512-byte bootloader and put it into the boot.ini as I mentioned earlier.  The install seemed to go just fine and asked me to reboot.  Of course I would not be able to boot to this Ubuntu yet because there would be no way to get to the boot loader on that partition yet.  I booted to WinXP and executed my BOOTPART software which seemed to work just fine because a 512-byte file which is supposed to be the boot loader from my fresh install of Ubuntu Studio 14.04 on partition 1 of the SATA drive was created as expected.

So I rebooted.  WinXP works just fine.  Ubuntu Studio 11.04 works just fine.  But if I choose the new Ubuntu Studio OS it does not work.  It says "cannot boot from hard disk.  Insert system disk and press any key".  

So I booted into Ubuntu Studio 11.04.  I can read all the files in my new partition, including the /boot/grub directory.  I have a piece of software in that Ubuntu called "Grub Customizer".  I thought I'd use it to put find the new Ubuntu and then I could choose Ubuntu 11.04 from the boot.ini menu, and from there boot into the new Ubuntu.  Grub Customizer surely finds the new Ubuntu and adds it to the menu.  It specifies the correct UUID.  But when I try my scenario of choosing Ubuntu 11.04 from the boot.ini menu and from there choosing the (newly added) Ubuntu 14.04 I get the following errors:  no such device [UUID]; no such disk; you need to load the kernel first.  The only other time I had these error was when I cloned an Ubuntu from one disk/partition to a different disk/partition in a different computer, and I fixed it by editing grub.cfg and fstab to specify the correct UUID, and it worked just fine.  But as I mentioned, the UUID in grub.cfg (on the Ubuntu 11.04 OS) matches the UUID of the partition.  I didn't check the grub.cfg on the new Ubuntu OS, but I can because it is readable from the old Ubuntu OS.

I realize this may have been addressed in pieces in various other posts, but I can't find it addressed all in one place.  Sorry if it's duplicated in part or in whole.  

But, any help here?

---

### Post by oldfred on 2016-02-11
Grub2 does not like to be installed to a PBR - partition boot sector. It normally complains about haveing to convert to blocklists or hard coded addresses which are unreliable. If address on drive is changed then boot fails.

I do not understand why you cannot just install grub2's boot loader to your new drive's MBR and use grub to boot. Then you still have your old (ancient) Windows boot in the Windows drive.

Grub does default to install to drive seen as sda, so with multiple drives only use Something Else to install as that is the only install option that gives choice on where to install grub2's boot loader.

Also with Boot-Repair, do not run any auto fix. That installs grub to every MBR and you do want to keep Windows on Windows drive. But you can run report and use the advanced mode to choose an operating system and drive to install boot loader.

       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Boot-Repair will only install or work on current versions, so install to live installer, not your old Linux install.

---

### Post by two4two on 2016-02-11
> **oldfred said:**
> Grub2 does not like to be installed to a PBR - partition boot sector. It normally complains about haveing to convert to blocklists or hard coded addresses which are unreliable. If address on drive is changed then boot fails.

I do not understand why you cannot just install grub2's boot loader to your new drive's MBR and use grub to boot. Then you still have your old (ancient) Windows boot in the Windows drive.



Thanks oldfred. :)

Doesn't my Ubuntu 11.04 use Grub2?  It's boot loader is in the PBS.  
Also, if I install to the new HD MBR wouldn't I have to change boot drive in BIOS (or BIOS pop-up) if I want to boot to there?  Are you saying install grub 2 to mbr of new disk and boot to the old Ubuntu and the WinXP from there?  Permanently change my boot disk?  

I'll see if I can do it, but there is no SATA controller on the mobo.  There is an add-in SATA controller.  It is an OLD PC.  So I'm not sure it can boot to this add-in card.  Interesting that the other 2 drives are on a different add-in card and the BIOS calls them SCSI drives and can boot there.  But they are IDE.  I don't know if the SATA on an add-in card will work as a boot drive with this BIOS/MOBO

I didn't want to install to boot device MBR because if things fail (as they are now) then NO OS could be booted.  There is no Win7 on this computer and so no "fixmbr" etc.  Could the fact it's a 32-bit machine and SATA 150 1TB have anything to do with it?  

I am going to do what you say with boot repair.  Also I'll list a bunch of other info (like BOTH grub.cfg and fstab, and another piece of software I have in the Ubuntu 11.04 that lists boot info (if I can remember what it is!).

---

### Post by oldfred on 2016-02-11
If system is that old, you may have issues booting from anything beyond an old IDE limit of 137GB on drive. All boot files must be in first 137GB.
I normally suggest a smaller / (root) of 25GB and either separate /home or /mnt/data partition or both to use rest of drive.

With Linux files are scattered (randomly?) in ext4 partition. And some then get system to boot, but a kernel update installs new kernel or grub file beyond the 137GB and system fails. Best to only have smaller / or separate /boot at beginning of drive if old BIOS.

---

### Post by two4two on 2016-02-11
> **oldfred said:**
> If system is that old, you may have issues booting from anything beyond an old IDE limit of 137GB on drive. All boot files must be in first 137GB.
I normally suggest a smaller / (root) of 25GB and either separate /home or /mnt/data partition or both to use rest of drive.

With Linux files are scattered (randomly?) in ext4 partition. And some then get system to boot, but a kernel update installs new kernel or grub file beyond the 137GB and system fails. Best to only have smaller / or separate /boot at beginning of drive if old BIOS.

The SATA drive is a 1TB drive divided into 4 partitions:  part 1 = 85GB EXT4 where the problematic Ubuntu is installed, part 2 = 85GB NTFS, part 3 = 85GB NTFS, and the rest of the drive (885GB) is NTFS.  It is a 32-bit machine.  All OSs are 32-bit OSs.  So the problematic Ubuntu is all in the first 85 GB of the device.  I will double check how much of the drive (all partitions) is usable by the working OSs.

---

### Post by oldfred on 2016-02-11
Unless extremely old BIOS where you only can change boot by moving the jumper pins on IDE hard drive, then you should be able to easily change boot in BIOS. And with SATA, you usually have a one time boot key like f10 or f12, check motherboard manual for correct key. Many old BIOS mention key as part of BIOS screen while booting.

And some have done the same as you have done, but copied MBR instead of PBR to boot from boot.ini. Not recommended, but another way.

---

### Post by two4two on 2016-02-11
I'll check into it all.  And I'll get some listings to post.  Thanks. :)

---

### Post by two4two on 2016-02-12
I've attached a boot-info report from boot-repair.  The ONLY thing I see that I might want to question is the start point of sdc1 partition which is where the problematic Ubuntu is installed.  There is also the boot.ini file which I use to do all the booting.  So it's like this:  sda has the controlling MBR; boot loader for boot.ini is sda1; sdb1 is WinXP; sdb3 is Ubuntu 11.04 and it's boot loader is in the partition; sdc1 is Ubuntu 14.04 and its boot loader is also in the partition.  The boot-info shows all this.  

So, I really hope someone can decipher all this and help me out.  My only idea is simply to re-install Ubuntu 14.04.  I do want to keep the boot loader in the partition.  But if all else fails then I guess I'll put it in the MBR for sdc and do my multi-boot from there if the BIOS will allow me to boot to that drive.

---

### Post by oldfred on 2016-02-12
Your sdc is a new 4K drive. Not sure if your old system can see that correctly or not.
When I purchased a SSD in 2011, I had to turn on AHCI in my BIOS, which then broke Windows. :) 
I dual booted for a few weeks to finalize shutdown of Windows as I could turn AHCI off & boot Windows, turn AHCI on and boot Ubuntu. 
SSD needed AHCI for trim to work, otherwise the older IDE mode would have worked.

       First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)

Since you have three drives you have three MBR, and should be able to install different boot loaders into each. I might use Something Else and reinstall to sdc, with grub2's boot loader installed to drive that is sdc.

Your 11.04, is long obsolete and cannot be updated. If not wanting to regularly reinstall use the LTS versions like 14.04 or 16.04 dual out in April.

---

### Post by two4two on 2016-02-13
So if I want to get the 512-byte boot loader from sdc1 what "dd" command would I use to get it?  Does the fact that in the other drives the first partition starts at 63, but on sdc the first partition (sdc1) begins at 2048 have anything to do with it?

PS:  I notice testdisk is in the MBR of sdb!  How in the world!  Since I don't boot to sdb it has never hurt me, but it is interesting.

---

### Post by oldfred on 2016-02-13
You must have told testdisk to install it. I think it is another Windows type boot loader.

Since Windows 7 and Linux soon after, all partitioning tools changed to use sector 2048 as start. No new drives should be formatted with the old sector 63. New 4K drives should use sector 2048 and 8 sector boundaries or else you slow drive down a lot. See links in post above.

I had archived this note, since I do not recommend it and no one uses it anymore.
You can backup your current mbr to a file. All you have to know is where you installed your grub. e.g. if you installed it into the mbr of your third harddrive (/dev/sdc), the command would be this, includes partition table, if partitions changed will cause major problems to recover:

sudo dd if=/dev/sdc of=/home/your_username/mbr.backup bs=512 count=1
Note that 512 includes partition table, may be better to use bs=446 which is just the boot code.

A partition boot sector is still the first sector of a partition, no matter what sector it starts on.

Part of issue may just be newer hardware (your drive) mixed with very old hardware.

---

### Post by two4two on 2016-02-13
Yep, I tried all of the above and it just won't boot.  Even boot-repar to install grub to MBR of sdc didn't work.  So I gave up and am cleaning out sda, deleting all but sda1, creating a new primary sda2 to fill rest of drive and moving the Ubuntu 14.04 to sda2.  Now I need to figure out how to close this thread.

---

