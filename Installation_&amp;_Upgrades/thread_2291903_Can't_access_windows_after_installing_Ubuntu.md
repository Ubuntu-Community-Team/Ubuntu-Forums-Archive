---
title: "Can't access windows after installing Ubuntu"
date: 2015-08-23
forum: Installation &amp; Upgrades
---

### Post by ghaedo on 2015-08-23
Hello,

I recently installed Ubuntu. I noticed that it didn&#8217;t give me the option to choose between Ubuntu and Windows. Currently, its only booting into Ubuntu and I cant get into Windows. Any help would be appreciated.

Here is my Disk-Repair URL: [http://paste.ubuntu.com/12179525/](http://paste.ubuntu.com/12179525/)

Thanks in advance!

Guido

---

### Post by yancek on 2015-08-23
> I recently installed Ubuntu. I noticed that it didn’t give me the option to choose between Ubuntu and Windows.

Do you mean when you reboot the boot menu does not show an option for windows?  If so, look at the boot repair output.  There are no windows filesystems so no windows partitions or operating systems.  I'm not sure which option you selected under Installation Type when installing Ubuntu.  The best giving most control is the manual method which is referred to as "Something Else" on screen.  Whichever option you selected, it wasn't the right one as it has overwritten your windows system.  Did you have a backup to another drive?  What's on the 20GB drive?  Was that an older windows install, it has windows code in the master boot record.

If you need to try to recover data that was overwritten, post back and someone will give suggestions.

---

### Post by ghaedo on 2015-08-24
> **yancek said:**
> Do you mean when you reboot the boot menu does not show an option for windows?  If so, look at the boot repair output.  There are no windows filesystems so no windows partitions or operating systems.  I'm not sure which option you selected under Installation Type when installing Ubuntu.  The best giving most control is the manual method which is referred to as "Something Else" on screen.  Whichever option you selected, it wasn't the right one as it has overwritten your windows system.  Did you have a backup to another drive?  What's on the 20GB drive?  Was that an older windows install, it has windows code in the master boot record.

If you need to try to recover data that was overwritten, post back and someone will give suggestions.

I chose the "something else" option. Then I created a 20GB partition and installed Ubuntu on the 20GB partition. The partition with over 400GB is where Windows is installed. Oddly enough before I went forward with Installing Ubuntu, the live CD couldn’t recognize another system installed on the hard drive and would say there is no other OS. I have a feeling that its a GRUB issue. Is there a way to replace GRUB with MBR or another method? Or maybe even a way to fix GRUB?

---

### Post by Bucky Ball on 2015-08-24
I have a feeling you've installed in legacy mode and Windows is installed in EFI. Please confirm.

Did you have Windows in hibernation mode when you installed? If so, if you can boot into it, boot into it and switch off hibernation, then reboot.

---

### Post by yancek on 2015-08-24
The fdisk output show only Linux filesystem on partitions.  However, since you are using GPT, fdisk is not always accurate.  The parted output below also shows only Linux filesystem partitions.

> Number  Start   End     Size    File system     Name  Flags
1      1049kB  2048MB  2047MB  linux-swap(v1)
2      2048MB  23.0GB  21.0GB  ext4
3      24.1GB  500GB   476GB   ext4


You haven't mentioned which windows you had installed.  If it was windows 8 or newer it was probably using UEFI/GPT and you would have needed to install Ubuntu in the same mode.  Doesn't look like that happened based on the output below which indicates no EFI or BIOS boot partition.

> sda	: GPT,	no-BIOS_boot,	has-no-EFIpart,

If you boot the Ubuntu install medium, open gparted and see if it gives any indication of a windows partition.  If you used the Something Else option and it didn't detect any operating system, that would have been a good time to stop.   Seeing that might have been because your windows was hibernated as suggested above.

---

