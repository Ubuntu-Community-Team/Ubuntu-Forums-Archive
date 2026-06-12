---
title: "what happens if I install Win XP on a new partition"
date: 2013-10-16
forum: Installation &amp; Upgrades
---

### Post by stephenbbb on 2013-10-16
I have a single partition hdd with Ubuntu now. I can create a new partition and install WinXP there and then recover grub.
Am I missing sth? There are vague warnings that Windows should be installed first. I do not want to waste the time to backup all data and re-install Ubuntu and spend time customizing it again.

---

### Post by Bashing-om on 2013-10-16
stephenbbb; Hi !

As I understand it, Windows wants to be installed onto that 1st partition(s). A Windows' bootloader finding the bootcode kind of thing .

[INDENT][INDENT]just my thought
[/INDENT][/INDENT]

---

### Post by stephenbbb on 2013-10-16
I think windows has no preference regarding partitions. It can be installed on a second partition or third.
But I have not done it and wanted to hear if smb has done that.

---

### Post by oldfred on 2013-10-16
The real requirement is that Windows must boot from a primary partition formatted NTFS with the boot flag.

Second installs can even be in a logical partition, but all boot files are in the primary partition with boot flag.

Some have had issues with Windows in a primary after the extended partition. Windows then may have some issues. So just make sure it is a primary partition in front of any logical partitions.

       Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)


 How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

---

### Post by coffeecat on 2013-10-16
First thing - Windows does **not** need to be installed in the first partition. If it is booting from a disc with an mbr (ms-dos) partition table, the boot files need to be in a primary partition with the boot flag set. This is normally accomplished in Vista and XP by having the C: partition as a primary, but it does not need to be the first primary. Quite a few OEM manufacturers used the first partition for a recovery partition and put the C: partition second. Things got slightly more complicated with Windows 7 which usually has a separate boot partition, but again so long as this is primary and has the boot flag set, it does not need to be the first, although it usually is.  

> **stephenbbb said:**
> I can create a new partition and install WinXP there and then recover grub. Am I missing sth? There are vague warnings that Windows should be installed first.

I would guess the "vague" warnings you've come across are to do with when you install Windows after Ubuntu, the Windows mbr gets written, overwriting grub code, and until you repair grub you can only boot into Windows. But you seem to be aware of that.

Less well known is the occasional damage the Windows installer can do to the partition table if there are pre-existing logical partitions formatted with a Linux filesystem. XP tries to "convert" the first logical partition to a primary, but still sitting inside an extended. Vista and later sometimes simply delete the first Linux logical partition. This doesn't always happen, and usually only when there are less than 3 primary partitions apart from the extended partition containing the logicals, but the potential for damage is there.

---

### Post by stephenbbb on 2013-10-16
quite informative guys, thank you.

so, since I have a single partition now with the bootflag set and it is a Linux partition do I need to set the boot flag on the second (NTFS) partition and if I do that then do I update-grub and install grub before the XP install? I will need to do it again after the XP install, of course.

---

### Post by coffeecat on 2013-10-16
Linux operating systems don't need the boot flag - it's only used for Windows. The Windows installer will set the boot flag to the partition you install Windows to. And Windows only needs the boot flag when booting from the Windows mbr. Once you have Windows booting as a chainload from a grub menu, it doesn't actually need the boot flag, although it won't do any harm.

There's no point in running update-grub and grub-install before you install Windows. But once you have installed Windows, you won't be able to boot into Ubuntu until you repair grub from a live CD/USB. Here's a useful link for you:

[https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2](https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2)

You say you have only one partition at the moment. No swap partition? You might want to post some details of your current and proposed partition layouts to see if there are any other points that need to be considered. Post the output of this terminal command:

```
sudo fdisk -lu
```

And/or a screenshot of Gparted.

---

### Post by stephenbbb on 2014-02-08
to coffeecat: this is the output. sorry for the delay. I had one reason for wanting to do this last year, and a different one now.

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ad76a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   614582639   307291288+  83  Linux
/dev/sda2       614582640   625137344     5277352+   5  Extended
/dev/sda5       614582703   625137344     5277321   82  Linux swap / Solaris

I do not recall ever creating an extended partition there. just ran the live intstall and never looked at it. Do I need to remove the extended and shrink sda1 to install windows there? 
Thank you
Stephen

---

### Post by oldfred on 2014-02-08
No, leave extended with swap. 
You have used 2 of the 4 allowed primary partitions with MBR as the extended counts as one primary.

Just shrink sda1 and create a new sda3. 
It may give messages in some tools about not in order, but that is not important that sda2 will be after sda3 on the drive.

If sharing Windows I usually suggest a smaller system partition and larger data partition. Usually best to set Windows system partition as read only and use another NTFS data partition for read/write data from both systems. If desired, you have room for sda4, as your last primary or can move the start of the extended left once you have made unallocated space to move some of the unallocated into the extended and put the NTFS shared data in the extended as another logical partition. Both Windows & Linux will read data from the logical NTFS without issue.

---

### Post by stephenbbb on 2014-02-11
I just need this to download some miniDV tapes. 1394 is not supported by Linux any more and XP is the only way to use a Firewire PCI card.
will use the first suggestion and report results here during the weekend.
Thanks everybody.

---

### Post by oldfred on 2014-02-11
Have you seen this?

[https://help.ubuntu.com/community/FireWire](https://help.ubuntu.com/community/FireWire)

---

### Post by stephenbbb on 2014-02-18
I found an old pre-sata 80gb drive in my garage and installed XP on that. have had trouble with dual boot from same drive using ubuntu for 6 years. 
when ubuntu upgraded to 58 it saw windows and gave me the grub menu on the restart. so I had to do nothing manually.

---

