---
title: "GRUB menu missing on dual boot"
date: 2018-04-26
forum: Installation &amp; Upgrades
---

### Post by Olivares on 2018-04-26
I have 64-bit desktop PC with Ubuntu 16.04 and Windows 8.1. I messed up my Ubuntu when I deleted files using FSlint Janitor, and decided to do a reinstallation. I reinstalled on the same partition as before. Machine now boots direct into Ubuntu, it does not display the GRUB menu. I have tried running Boot Repair, but it gives me a message about entering commands into a terminal, the first of which is: sudo chroot "mnt/boot-sav/sda6" dpkg -configure -a. (Ubuntu is actually installed on sdb6). The error message I get in response is: "cannot change root directory to /mnt/boot-sav/sdb6: no such file or directory." (The mnt directory has nothing in it).

Boot Information Summary can be viewed here: [http://paste.ubuntu.com/p/wPrnwFbsHJ/](http://paste.ubuntu.com/p/wPrnwFbsHJ/) . 

In case it is helpful, UEFI setup boot options shows the following:

1. SATA: HL-DT-ST DVDRAM GH24NSBO
2. UEFI: Built in EFI Shell
3. UEFI: Seagate Backup + Desk 0342
4. Disabled

Apparently Windows Boot Manager is supposed to be an option here, but I don't see it.

---

### Post by Roger_Williams on 2018-04-26
[COLOR=#000000][FONT=monospace]did you try running sudo update-grub it should search and update the Grub menu with all installed OSes

[/FONT][/COLOR]

---

### Post by oldfred on 2018-04-26
I am surprised it installed.
```
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


```

It looks like then you have a newer system that had Windows in UEFI/gpt boot mode. But reinstalled Windows in BIOS boot mode. Windows does not correctly convert gpt to MBR(msdos) and leave a backup gpt partition table.
You need to remove backup gpt table as both installs are BIOS/MBR.
       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
sudo fixparts /dev/sda 

Did you leave Windows fast start up on?
The Linux NTFS driver will not mount NTFS that is hibernated & fast start is really just hibernation.
And with BIOS it is a bit of a hassle to get to Windows to turn it off.
Grub only boots working Windows, or Windows that is not hibernated nor if it needs chkdsk.
So you have to temporarily restore a Windows BIOS boot loader, fix Windows and then restore grub every time you have Windows issues. And Windows with updates will in background turn fast start up back on. 
With UEFI you just need to directly boot Windows and then from UEFI boot Ubuntu entry, much easier.

While Boot-Repair does not fix most Windows issues, it can install a Windows BIOS boot loader to MBR, but it may not see Windows to let you fix it?
      
 How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

---

### Post by Olivares on 2018-04-27
Thank you for your replies. I have installed fixparts; when I tried your command it asked me to choose from the following options:
toggle the active/boot flag
recompute all chs values
set partition as logical
omit partition
print the mbr partition table
quit without saving changes
set partition as primary
sort mbr partitions
change partition type code
write the mbr partition table to disk and exit.

I didn't know what to do so exited.
I can confirm Windows fast boot up is turned off.

---

### Post by oldfred on 2018-04-27
If fixparts did not see both MBR & gpt and offer to write partition table correctly then I do not know where the fdisk warning came from?

Did you try restoring the MBR boot loader?

---

### Post by Olivares on 2018-04-28
OK, if I am to attempt restoration of the MBR boot loader I want to make sure I have got things right.
Firstly, FYI here is the details of the partitions I have:

Disklabel type: dos
Disk identifier: 0x9a8aa40c


Device     Boot Start       End   Sectors  Size Id Type
/dev/sda1  *     2048 488378644 488376597  1.8T  7 HPFS/NTFS/exFAT




Disk /dev/sdb: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x1f9c02ef


Device     Boot      Start        End   Sectors   Size Id Type
/dev/sdb1             2048     718847    716800   350M  7 HPFS/NTFS/exFAT
/dev/sdb2  *        718848  979451903 978733056 466.7G  7 HPFS/NTFS/exFAT
/dev/sdb3        979453950 1953523711 974069762 464.5G  5 Extended
/dev/sdb5       1939007488 1953523711  14516224   6.9G 82 Linux swap / Solaris
/dev/sdb6        979453952 1939006686 959552735 457.6G 83 Linux


Partition 3 does not start on physical sector boundary.
Partition table entries are not in disk order.

The 'restore MBR' option of Boot Repair lists 18 options for which MBR to restore: sda (generic mbr), sda (generic mbr_c) ... sdb (generic mbr) etc.
Then there are four options for 'partition booted by': sda2 (Windows 8), sda1 (Windows 8 (boot)), sda6 (Ubuntu 16.04 LTS), and sdb1.

Am I correct in thinking that the options to choose are (a) sdb (generic mbr) and  (b) sdb1?

---

### Post by oldfred on 2018-04-28
Do not install grub to partition. Best with multiple drives to just have grub in the same drive sda, sdb as Ubuntu. And if other installs in other drive keep its boot loader in that MBR.

I prefer newer UEFI as then you have the equivalent of multiple MBR as each install has its own folder in the ESP - efi system partition for booting.

---

### Post by Olivares on 2018-04-28
I went through restoration of MBR boot loader procedure, it has made no difference (still no GRUB menu).

'GRUB options' in Boot Repair has the following two options:
  OS to boot by default. The options it offers are: sda6 (Ubuntu), or Windows (via sda6 menu)
  Place GRUB into: Options are: sda or sdb.

But Ubuntu (and Windows) are on sdb, not sda.

A new Boot Info Summary is at [http://paste.ubuntu.com/p/y9YMYPqVcT/](http://paste.ubuntu.com/p/y9YMYPqVcT/). It shows that Grub2 is installed in the MBR of sda. Sda is the external hard drive used for backup.

---

### Post by Olivares on 2018-04-28
I ran command sudo grub-install /dev/sdb. This did not make the grub menu automatically appear on bootup, BUT the menu does appear if I hold down the SHIFT key. So I now that I have access to Windows (where I do my professional work) I guess I have a solution.

Any comments?

---

### Post by oldfred on 2018-04-28
Based on report sda is internal drive and sdb is Seagate Backup drive.

You want to reinstall grub to MBR of Ubuntu drive.
You may need to do the full install/reinstall of grub2 if just reinstalling to MBR does not work.

---

### Post by Olivares on 2018-04-28
Why does boot info summary say installation is on sda when output of fdisk -l says the installation is on sdb? Are you sure sda is the correct drive to install grub on? 

I did say in my previous message that I had managed to make the GRUB menu appear. However, after that, I shut down the PC, restarted after a break, and then found that the GRUB menu did NOT appear, with or without holding down the SHIFT key.

---

### Post by oldfred on 2018-04-28
If you rebooted between running commands, drive order can change.
Mine regularly changes when I plug in a USB flash drive as sdc, but on reboot flash drive is sda and every other drive has moved up a letter.

---

### Post by Olivares on 2018-04-29
Several hours later ... I went for the 'restore MBR' option in Boot Repair, PC now boots direct into Windows. Presumably I can revert to Ubuntu if I run Boot Repair again, and go for the 'repair GRUB' option.

---

### Post by Olivares on 2018-04-30
A colleague referred me to the following:
[https://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd](https://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd) 
Followed these instructions and problem is now solved.

---

