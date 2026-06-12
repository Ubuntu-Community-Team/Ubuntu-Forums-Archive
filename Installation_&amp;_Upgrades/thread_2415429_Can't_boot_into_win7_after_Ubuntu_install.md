---
title: "Can't boot into win7 after Ubuntu install"
date: 2019-03-25
forum: Installation &amp; Upgrades
---

### Post by william-s2 on 2019-03-25
Hello,
I installed Ubuntu 18.04 on a separate SSD drive a few months back. I left win7 on a separate drive ( for one program I need from time to time ). Today was the first day, I tried to boot to windows, but it doesn't work, just bounces me back to Grub. 

I know I could take the Win7 DVD, boot from that, and repair the boot sector, and windows would rewrite the boot sector, then I might not be able to get back to Ubuntu??

Does anyone know a better solution?

Any tips appreciated.

---

### Post by oldfred on 2019-03-25
May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by william-s2 on 2019-03-26
Cool, thanks for the reply. 
Since I can still boot into Ubuntu just fine, could I also just run Boot-Repair from here?
I'll be out of town till late for work, I'll try it when I get back.

---

### Post by william-s2 on 2019-03-26
OK. I think I made it one step worse, I ran the boot repair program from Ubuntu install and now it skips grub and goes straight to login screen.

Boot log at following link:

[http://www.ponopolis.com/Boot-info_20190326_1202.txt](http://www.ponopolis.com/Boot-info_20190326_1202.txt)

---

### Post by oldfred on 2019-03-26
Your sda drive shows gpt partitioning & an ESP, but no Windows boot entries.
Windows only boots in UEFI mode from gpt partitioned drives.

Your other two drives, sdb & sdc are the old MBR(msdos) partitioning, but you installed Ubuntu in UEFI mode to sdc. Better if sdc was gpt.
If you have not done much, I would reinstall. And even if you have, I would backup /home and reinstall & restore /home. So drive can be gpt.

You can run Windows repairs using your Windows repair flash drive or installer with recovery/repair console. That is the only way to fix Windows as Boot-Repair is primarily for Linux repairs.If you have backup of sda's ESP, you can also restore that, and then add Windows UEFI boot entry with efibootmgr.
[https://superuser.com/questions/460762/how-can-i-repair-the-windows-8-efi-bootloader](https://superuser.com/questions/460762/how-can-i-repair-the-windows-8-efi-bootloader)

       Windows 10 repair disk
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)

---

### Post by william-s2 on 2019-03-26
Thanks a lot for your help. I guess you're right. I'll just back-up and reinstall everything. I only need Win7 with one program and a few plug-ins. Though, I'm a bit of a noob with the UEFI, how do a set that up, and gpt on the Linux drive? Do I do that in the BIOS?

---

### Post by oldfred on 2019-03-26
If just installing from scratch and you boot in UEFI boot mode, drive will be gpt.
If you partition in advance, you use gparted but have to select gpt before adding any partitions. 

Both Windows & Ubuntu install in the boot mode you use for installer, so for UEFI always boot install media in UEFI boot mode.

With UEFI Windows always wants multiple partitions:
       BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx) & 
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations) 
    
I like to include an ESP - efi system partition (FAT32) on every drive as first partition, even if not currently used.

Older instructions may still mention swap partition, but 18.04 uses a swap file, so no swap partition required.
       [https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace) 
    
       UEFI/gpt partitioning in Advance:
[http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu](http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu)

See link in my signature below for (too much) info on UEFI.

---

### Post by william-s2 on 2019-03-26
OK. Thanks. I'll read up a bit, and give it a try.
I'll have to wait a week, or two, till I have time to reinstall everything.
Wish me luck, and thanks again.

---

