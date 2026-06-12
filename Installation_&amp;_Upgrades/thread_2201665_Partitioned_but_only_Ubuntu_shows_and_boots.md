---
title: "Partitioned but only Ubuntu shows and boots"
date: 2014-01-25
forum: Installation &amp; Upgrades
---

### Post by mom1mom1 on 2014-01-25
When I start up, there is no Windows to boot from, however I have this in GParted showing it is there.  I do not know exactly what was done to get to this point; trying to figure out for someone.  Said something about formatting and then formatted to ntfs then tried something else and "flag" disappeared and got the "Media.." in a column.  When turn on computer goes to Ubuntu.  Live USB is removed.  No choice of operating systems.

This is what I have.  It has been years since installed any linux and a novice still but can follow directions.

Thank you kindly,

---

### Post by fantab on 2014-01-25
Your screenshot is not working.

can you post the output of:

```
sudo parted -l
sudo fdisk -l
```

---

### Post by mom1mom1 on 2014-01-25
> **fantab said:**
> Your screenshot is not working.

can you post the output of:

```
sudo parted -l
sudo fdisk -l
```


Model: ATA TOSHIBA MK1655GS (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  88.2GB  88.2GB  primary   ntfs         boot
 2      88.2GB  160GB   71.8GB  extended
 5      88.2GB  160GB   71.8GB  logical   ext4

---

### Post by fantab on 2014-01-25
Please post the complete output of both commands, also Run and post the output of:

```
sudo update-grub
```

---

### Post by mom1mom1 on 2014-01-25
Model: ATA TOSHIBA MK1655GS (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  88.2GB  88.2GB  primary   ntfs         boot
 2      88.2GB  160GB   71.8GB  extended
 5      88.2GB  160GB   71.8GB  logical   ext4

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005c47c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   172289853    86144895+   7  HPFS/NTFS/exFAT
/dev/sda2       172292094   312580095    70144001    5  Extended
/dev/sda5       172292096   312580095    70144000   83  Linux

**sudo update-grub** 

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.8.0-29-generic
Found initrd image: /boot/initrd.img-3.8.0-29-generic
Found linux image: /boot/vmlinuz-3.2.0-58-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-58-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
done

---

### Post by mom1mom1 on 2014-01-25
> **fantab said:**
> Please post the complete output of both commands, also Run and post the output of:

```
sudo update-grub
```

Hope I got the right stuff this time!  Posted info/comment just above this Thank you!

---

### Post by fantab on 2014-01-25
Grub is not detecting Windows.

I don't see anything wrong with your partitions either, but for this:

```
Device Boot      [COLOR=#b22222]Start[/COLOR]         End      Blocks   Id  System
/dev/sda1   * **[COLOR=#b22222]         63[/COLOR]**   172289853    86144895+   7  HPFS/NTFS/exFAT
/dev/sda2       172292094   312580095    70144001    5  Extended
/dev/sda5       172292096   312580095    70144000   83  Linux
```

Your first partition /dev/sda1- NTFS (Windows) starts at '63'. It should start at a number divisible by 8 or a multiple of 8. 
So '64' is a good number but not '63'. Ideally it should start at '2048'.

Download and install Gparted in Ubuntu. And adjust the 'start' of /dev/sda1 to start at a number divisible or multiple of 8.
After the adjustment re-run 'sudo update-grub' to see if Windows is detected by grub.

However if for some reason your copy of Windows is corrupt then, you probably need to re-install Windows or repair it.
If there is DATA to be rescued from Windows then you can do so from Ubuntu. 
BACK UP your DATA before you do anything.

---

### Post by mom1mom1 on 2014-01-26
> **fantab said:**
> Grub is not detecting Windows.

I don't see anything wrong with your partitions either, but for this:

```
Device Boot      [COLOR=#b22222]Start[/COLOR]         End      Blocks   Id  System
/dev/sda1   * **[COLOR=#b22222]         63[/COLOR]**   172289853    86144895+   7  HPFS/NTFS/exFAT
/dev/sda2       172292094   312580095    70144001    5  Extended
/dev/sda5       172292096   312580095    70144000   83  Linux
```

Your first partition /dev/sda1- NTFS (Windows) starts at '63'. It should start at a number divisible by 8 or a multiple of 8. 
So '64' is a good number but not '63'. Ideally it should start at '2048'.

Download and install Gparted in Ubuntu. And adjust the 'start' of /dev/sda1 to start at a number divisible or multiple of 8.
After the adjustment re-run 'sudo update-grub' to see if Windows is detected by grub.

However if for some reason your copy of Windows is corrupt then, you probably need to re-install Windows or repair it.
If there is DATA to be rescued from Windows then you can do so from Ubuntu. 
BACK UP your DATA before you do anything.

Thank you for responding.  I have Gparted already installed; only thing is I cannot find a way to change the 'start' number.  The 'partition' tab is shaded/blocked for resize/move.  Should I look someplace else?

---

### Post by fantab on 2014-01-26
I don't understand what you mean. 
Take a look at this tutorial: [http://www.dedoimedo.com/computers/gparted.html#mozTocId335513](http://www.dedoimedo.com/computers/gparted.html#mozTocId335513)

Start Number 63 is in MiB. So you will adjust the MiB

---

### Post by mom1mom1 on 2014-01-26
> **fantab said:**
> I don't understand what you mean. 
Take a look at this tutorial: [http://www.dedoimedo.com/computers/gparted.html#mozTocId335513](http://www.dedoimedo.com/computers/gparted.html#mozTocId335513)

Start Number 63 is in MiB. So you will adjust the MiB

Gparted has "resize/move" option in light letters that are not clickable.  Only "unmount" and "manage flags" are clickable.  I have made sure Gparted is updated.  Does it have anything to do with their being an icon sahped as a key  next to "/dev/sda1?  Unmount first?  Thank you kindly.

---

### Post by sudodus on 2014-01-26
yes, unmount first :-)

---

### Post by oldfred on 2014-01-26
Starting at partition 63 is the old standard with XP and older versions of Ubuntu. It was/is the new 4K drives and SSDs where the partition start being on 8 sector boundaries is critical.

Any change to Windows NTFS partition size requires chkdsk, as it has to have the same start & size info in its PBR or partition boot sector as the partition table. 

May be better to see if any obvious errors are in Windows. But Boot-Repair can only make minor repairs to Windows  boot issues and usually a Windows repairCD or flash drive is required.

       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by mom1mom1 on 2014-01-26
> **oldfred said:**
> Starting at partition 63 is the old standard with XP and older versions of Ubuntu. It was/is the new 4K drives and SSDs where the partition start being on 8 sector boundaries is critical.

Any change to Windows NTFS partition size requires chkdsk, as it has to have the same start & size info in its PBR or partition boot sector as the partition table. 

May be better to see if any obvious errors are in Windows. But Boot-Repair can only make minor repairs to Windows  boot issues and usually a Windows repairCD or flash drive is required.

       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)


Using Windows xp professional and ubuntu 12.04. 

Here are boot reports:

[http://paste.ubuntu/6821731/](http://paste.ubuntu/6821731/)

and

[http://paste.ubuntu.com/6821741/](http://paste.ubuntu.com/6821741/)

I did reboot and although did not get Windows at least their were some choice.  It did not give me much time to copy.  First was ubuntu, second was previous ubuntu; either or both of these could have said Linux.  The third was memory test, the forth was memory test with something else added.  I can reboot again and try to catch more specific verbage.

---

### Post by oldfred on 2014-01-26
You are not showing any boot files at all in your NTFS partition.

 Windows BIOS Boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM
Vista/7/8 (with 7or 8 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe 

Normally you see those in the sda1 entry at the top of the bootinfo report as that is the partition with the boot flag.
Did you have another Windows install and move boot flag? Windows only installs boot files into the active partition with the boot flag, so any other installs do not have boot files.

---

### Post by mom1mom1 on 2014-01-26
> **oldfred said:**
> You are not showing any boot files at all in your NTFS partition.

 Windows BIOS Boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM
Vista/7/8 (with 7or 8 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe 

Normally you see those in the sda1 entry at the top of the bootinfo report as that is the partition with the boot flag.
Did you have another Windows install and move boot flag? Windows only installs boot files into the active partition with the boot flag, so any other installs do not have boot files.

I am not sure what was done.  I have been told it was Windows xp.  Installed mint, could dual boot.  Did not like mint so installed over it lubuntu and then they could not find windows. In Gparted they reformatted to from ntsf to fat32 (who knows why; they thought that was was some formu was telling them to do).  But still nothing so they installed ubuntu.  Somewhere in their trying everything but anything they changed it back to ntfs and that mysteriously (to them) put /media/sda for mount point. They also did something in the flag column but they can't explain or remember, probably because they were having the blind lead the blind. The same windows has been on the computer for years.  No repair disk even.  By the time I got the story, my head was spinning and came directly here! :)   I imagine everyone would be happy if I could get windows docs and stuff retrieved.  However, now I feel challenged and so, so, so want to get this.  It is new to me, although I was familiar with linux years ago but only as a novice, I would like to learn from this.  Thank you for helping me in my determination.

---

### Post by oldfred on 2014-01-26
Have you tried just mounting the NTFS partition with Nautilus and its defaults? It may show by UUID (long number) or by some id like 80GB drive?
Do it show an error?

If you get errors you at least need to run chkdsk. And if you have an XP disk you can use that. I have used newer Windows 7 repairCD to run chkdsk on XP install, but they cannot always run other fixes.

Some third party repairCD may also be able to run Windows chkdsk or other fixes.
       Third party chkdsk tools

 Hiren's Boot CD, and do a chkdsk on the XP
 [http://www.hirensbootcd.org/](http://www.hirensbootcd.org/)


Also has chkdsk and some other Windows repairs in free version:
[http://www.partitionwizard.com/features.html](http://www.partitionwizard.com/features.html)

   EASEUS Partition Master 
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)

---

### Post by mom1mom1 on 2014-01-26
Nautilis?  Might need direciton in this.  One thing, I looked at the info I pasted above on UEFI boot install % repair.  Does it mean anything that the Windows is xp professional and the log reads, 
    Boot sector type:  Windows Vista: NTFS  Or does Vista here not refer to os?  Back to Nautilis, I went to softwares to see what it was and there
are several different Nautilis programs; I spent time googling and going over the boards trying to figure out to do your suggestion and I fear I am going in 
circles. Your links have been very helpful.

---

### Post by oldfred on 2014-01-26
NTFS partitions have a PBR which is like a MBR to a hard drive. The PBR or partition boot sector may also contain boot code. With Windows it will refer to ntldr with XP or bootmgr with Vista or later. Not sure how Boot-Repair tells then whether Windows 7 or 8 but it also shows those. So there are some differences to PBR.

Nautilus is the file browser (like Windows explorer) in full Ubuntu, If not running Lubuntu you will not have Nautilus but a different file browser.

My screenshot does not show XP, but it may be UUID, or size based, but should be an entry in the left panel under Devices like this screenshot.

---

### Post by mom1mom1 on 2014-01-26
Ok.  Before I start doing all sorts of trial and errors, is there a way, in my situation to get my windows docs into ubuntu? or on a flashdrive?

---

### Post by oldfred on 2014-01-27
NTFS partition has to be mounted. And the chkdsk flag or hibernated flag prevent mounting so that you do not cause more damage that a Windows chkdsk may then not be able to fix.

If Nautilus or your file browser will not auto mount it. <device-name> is sda1 for you. Note space after after <device-name>.        

sudo mkdir /media/windows
sudo mount ntfs-3g -o rw /dev/<device-name> /media/windows
if you get a message regarding Windows not being shutdown properly, then run the following command to force the mount
But better to run chkdsk from a Windows repair CD first, only use this if you have to copy data.
sudo mount ntfs-3g -o force,rw /dev/<device-name> /media/windows

---

