---
title: "Dual Boot Win 8.1 (MBR) &amp; Ubuntu 12.04.3, 2 HDD"
date: 2013-12-06
forum: Installation &amp; Upgrades
---

### Post by chaosnated on 2013-12-06
Hi there,

I want to dual Windows 8.1  (MBR) & Ubuntu 12.04.3. Both are x64 version. I have 2 HDD with following structure:

> /dev/sda
/dev/sda1 (NTFS) = Windows 8.1 system drive
/dev/sda2 (NTFS) = Windows 8.1 boot loader
/dev/sda3 (NTFS) =
/dev/sda4 (NTFS) =

/dev/sdb
/dev/sdb1 (NTFS) =
/dev/sdb2 (NTFS) =
/dev/sdb3 (EXT4) = Here i want to install Ubuntu

Now what I like to do is, I want to boot to each individual OS by using system boot device menu i.e it should normally boot direct to Win 8.1 and when I want to boot to Ubuntu, I'll be using my F11 Boot Key then selecting HDD 2.

Is it possible to do this?


**Regards~**

---

### Post by oldfred on 2013-12-06
You mention MBR(msdos) so both drives are MBR and not gpt?

You should make sdb4 an extended partition and have your logical ext4 and swap inside the extended. Only with logical partitions can you have more than 4 partitions because of the primary partition limit with MBR.

You will need to use Something Else or manual install as that is the only install option that has the extra combo box at the bottom of the partitioning screen on where to install the grub2 boot loader. You want grub in sdb not sda. It can be fixed later but better to install directly to sdb.

I prefer to partition in advance, but with manual install you can create partitions. Either way you have to choose change and select format like ext4 and mount point like / (root). If you have created swap beforehand it will auto find it, otherwise you need to also create swap but it has no format.

My screen shot shows me overwriting an older install that was previously labeled in sdc, but I have grub still defaulting to sda.

---

### Post by chaosnated on 2013-12-06
Yes, both HDDs are MBR as my PC is old & doesn't EUFI. I have unallocated space on my sdb and from this space I will b making making 'sdb3 ext4 (for root)' & 'sdb4 swap'.

Now what should I create sdb3 & sdb4 as, primary or logical? Little confused here :/

---

### Post by ajgreeny on 2013-12-06
Use logical partitions inside an extended partition; it is much more flexible a way to do the job, and Linux will boot just fine from a logical partition, unlike windows which needs a primary partition.

---

### Post by oldfred on 2013-12-06
You can only have 4 primary, normally swap is logical but may be better to have both / & swap as logical. Then you have available for future use additional primary partitions. Once you have used all 4 primary, it can be difficult to reorganize.
I normally use one or two primary partitions at beginning of drive and then make entire rest of drive (most of it) as an extended partition, so I can have many logical partitions.

---

### Post by chaosnated on 2013-12-07
> **oldfred said:**
> You can only have 4 primary, normally swap is logical but may be better to have both / & swap as logical. Then you have available for future use additional primary partitions. Once you have used all 4 primary, it can be difficult to reorganize.
I normally use one or two primary partitions at beginning of drive and then make entire rest of drive (most of it) as an extended partition, so I can have many logical partitions.

I made 2 partitions:

sdb5 logical as 2GB swap
sdb6 logical as 10GB root

&  install boot loader in sdb6 then started installation. When all was  done I restarted and  used F11 to boot from 2nd HDD (which is sdb), but  now I'm getting BootMGR is missing.

Win 8.1 boots normally without using using F11 key. Now how can I boot to Ubuntu? Please guide me as noobie in Linux based OS, my 1st time Ubuntu hehe.

---

### Post by oldfred on 2013-12-07
With BIOS/MBR you only have one boot loader in the MBR. BIOS jumps to MBR to start booting and since MBR is tiny it really just jumps to more boot code somewhere else on drive.
So you cannot install grub2's boot loader to a Partition Boot sector unless you have another boot loader that boots other systems. Windows only boots Windows.
So install grub2's boot loader to the MBR and then from grub menu, you can choose to boot Ubuntu or Windows. You will have to keep fast boot or always on hibernation off, as Windows does not seem to recover from that when booted from grub.

       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by heir4c on 2013-12-07
Grub must be installed on sdb (in your situation) and not on sdb6. When you install Ubuntu and you see the partition manager you have the option to choose where you put Grub (bootloader) See the second screenshot from oldfred. At the bottom of the window you see under the + - and change the following line: Device for boot loader installation. With the button below you can choose the place to install Grub. And here you must choose: sdb. Then you can boot up with the second HD from out the Bios-boot-menu. (in your case F11)
[http://ubuntuforums.org/showthread.php?t=2192202&p=12866792#post12866792](http://ubuntuforums.org/showthread.php?t=2192202&p=12866792#post12866792)

---

### Post by chaosnated on 2013-12-08
> **heir4c said:**
> Grub must be installed on sdb (in your situation) and not on sdb6. When you install Ubuntu and you see the partition manager you have the option to choose where you put Grub (bootloader) See the second screenshot from oldfred. At the bottom of the window you see under the + - and change the following line: Device for boot loader installation. With the button below you can choose the place to install Grub. And here you must choose: sdb. Then you can boot up with the second HD from out the Bios-boot-menu. (in your case F11)
[http://ubuntuforums.org/showthread.php?t=2192202&p=12866792#post12866792](http://ubuntuforums.org/showthread.php?t=2192202&p=12866792#post12866792)

Thanks there. I did the experiment in Virtualbox and figured this out too about what I did wrong. I didn't select the disk, selected partition to install GRUB2 instead. Now I will do a reinstall to fix this. I know I can use Boot-Repair LiveCD to relocate GRUB2 from sdb6 to sdb too.

---

### Post by chaosnated on 2013-12-08
Another question, when I use sdb as GRUB2 Bootloader, will I be able to use NTFS partitions sdb1 & sdb2 in Win 8.1?

---

### Post by heir4c on 2013-12-08
Normally Yes, You will see this partitions in the Filemanager in Ubuntu and Windows and in the Grub-menu you will see the Windows on your first HD too. So if you want you can boot up from there with Windows.

---

### Post by oldfred on 2013-12-08
If you use Boot-Repair do not run the auto fix. It will install grub to both sda & sdb. You want to keep the Windows boot loader on sda. Select advanced options and choose the install and the drive to install a boot loader into. 
If you already ran the auto repair, you can install a Windows boot loader to sda the same way.
You then change BIOS to auto boot sdb first. Only if you have issues with sdb, then in BIOS or one time boot key you can directly boot Windows from sda.
If Windows is hibernated or fast boot is on, the only way to boot Windows would be the one time boot key or have BIOS set to boot sda and only choose Ubuntu from one time boot key. Grub is both a boot manager and a boot loader. But using one time boot key you are not using the boot manager features.

---

