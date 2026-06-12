---
title: "Resize Partition -&gt; Windows boot disapear"
date: 2017-08-21
forum: Installation &amp; Upgrades
---

### Post by quentinous on 2017-08-21
Hello,

I had Windows 10 - Windows 7 and Mint 17 (Ubuntu 14). I remove Windows 7 which was on the same hdd with my Linux, in order to resize linux partition.
Grub is booting, I can go on my linux but windows 10 is lost. Can you help me ?
here my pastbin:

[http://paste.ubuntu.com/25362331/](http://paste.ubuntu.com/25362331/)

Many thanks

---

### Post by Bucky Ball on 2017-08-21
Welcome. Boot into Ubuntu, open a terminal and issue this:

```
sudo update-grub
```

Reboot. Do you now get Windows showing in the grub menu? If so, select it and see if it is now booting correctly.

---

### Post by oldfred on 2017-08-21
Is your Windows sdb1?

Windows normally only boots from one primary NTFS formatted partition with the boot flag.
And the BCD in the first install then will add any other installs you have. So you BCD in Windows 7 was probably updated to really be the Windows 10 boot files & added the Windows 7 as another entry.

You seem to only be missing a BCD in sdb1 as you have bootmgr. 
But Windows will not repair it unless it also has boot flag, or is using your Windows repair disk the make active command. Some Windows third party tools also will create a new BCD, but you cannot do those repairs from Linux. You may also need chkdsk and should install a Windows boot loader to sdb, since you have grub on other drives to boot. But occasionally you may need to directly boot Windows from BIOS by  selecting sdb. Grub only boots working Windows.

This may or may not be an issue as reported by Boot-Repair (sfdisk).
>  WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util sfdisk doesn't support GPT. Use GNU Parted. 



Windows only boots from gpt with UEFI.
And Windows only boots in BIOS boot mode from MBR(msdos) partitioning. But if you install Windows to a gpt partitioned drive in BIOS mode it incorrectly converts gpt to MBR leaving the backup gpt partition table. Windows seems to then ignore backup gpt, but Linux tools see backup gpt & primary MBR and get confused and only offer to erase drive to convert to one or the other.

If now really MBR, best to remove backup gpt with fixparts.
       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
sudo fixparts /dev/sdb

---

