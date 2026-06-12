---
title: "Ubuntu cannot see partitions"
date: 2012-02-12
forum: Installation &amp; Upgrades
---

### Post by nimraynn on 2012-02-12
Hi there,

I'm having some problems installing Ubuntu Desktop 11.10 onto my PC. I would like to do a dual boot with my existing Windows 7 installation, but it appears to be having problems seeing the partitions.

My first attempt at installing Ubuntu, I used the Wubi installer as it looked a lot simpler than any other installation I've ever done before and did exactly what I wanted... but after it appeared to be quite successful, it rebooted and started to boot into Ubuntu and then gave me the following error:

> No root file system is definedI tried rebooting again, tried uninstalling and reinstalling it, all to no avail... so I decided it woul dbe better if I did it properly. Boot from the CD, sort out the partitions and install it that way.

So I boot from the CD, and it doesn't see anything at all on the partitions. It tells me my whole drive is unallocated... but I know for a fact I've got a 250GB partition and a 1250GB partition on the drive, both NTFS. Ideally, I want to resize the 1250GB partition and create a new Ubuntu partition, but it claims I haven't got anything at all!

After some Google searching, I have seen some suggestion to use GPT fdisk, but I don't really know what I'm doing with this and I'm getting a bit lost.

Does anyone have any suggestions on how I can resolve the issue without losing any data on my drive? I have backups, but I'd rather not lose anything if I can avoid it.

I'm quite technically minded, but a bit of explanation would be nice for any suggestions. I'm an MCDST and could fix many issues on a Windows installation without much hesitation, but when it comes to Linux, I'm not hugely clued up. :)

Cheers,
Mike.

---

### Post by westie457 on 2012-02-12
Hi am also a bit lost when it comes to GPT partition tables as well.

Any way shall we make a start on this?

Boot into a LiveCD/USB Desktop - ie 'TRY' mode and post the output of ```
sudo fdisk -l
``` the l is a small L not a 1 or a small I.

Also go to this site [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

and follow the instructions to download, run and post the final RESULTS.txt file.

This should tell us what is what with your system.

Thank you

---

### Post by nimraynn on 2012-02-12
Hi there,

Thank you for the quick reply. I will give that a go, however I appear to have another issue now which I didn't seem to have earlier this morning...

I have completely shut down the system (last booted into Windows 7), turned it back on and placed the Ubuntu CD in the drive. It appears to boot OK, asks me if I want to Try or Install, so I click the Try button. It then thinks for a second, then both my monitors just go into sleep mode and nothing more happens. It sounds like there is some sort of CD activity, but nothing happens.

Any ideas why this might be? The system is based on an AMD Phenom II X6 1090T with a Gigabyte GeForce 560 graphics card if it makes any difference.

Thanks.

---

### Post by nimraynn on 2012-02-12
Ok, not quite sure what I did but I pressed some buttons, things happened and now it books OK :confused: Only one screen of the two works, but still boots...

So here is the result I get back from sudo fdisk -l:

[IMG]http://www.nimraynn.co.uk/stuff/ubuntu1.png[/IMG]

And then this is what comes from the results of the Boot Info Script:

>                   Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   524,494,847   524,288,000   7 NTFS / exFAT / HPFS
/dev/sda3         524,494,848 2,930,274,303 2,405,779,456   7 NTFS / exFAT / HPFS


GUID Partition Table detected, but does not seem to be used.

Partition    Start Sector    End Sector  # of Sectors System

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        1EBA4E8DBA4E617F                       ntfs       System Reserved
/dev/sda2        06BE7C9EBE7C87C7                       ntfs       
/dev/sda3        F6B241BBB24180DB                       ntfs       Data

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)




Doesn't mean much to me I'm afraid :(

This is what gParted shows:

[IMG]http://www.nimraynn.co.uk/stuff/ubuntu2.png[/IMG]

Any ideas?

Thanks again!

---

### Post by darkod on 2012-02-12
The message that GPT table was detected means there is some remaining of GPT table. Because according to the fdisk results your partitions are msdos.
What probably happened is that the disk came with gpt table, but you changed it to msdos. When you do that in windows, it seems it changed the partition table, but in fact doesn't delete the backup gpt table (which all gpt disks have).

So for linux, it creates confusion whether the disk is msdos or gpt because it sees both tables, the main one, and the undeleted gpt backup.

And in case it can't see things correctly, Gparted doesn't show any partitions for your protection, because it can't see what is what.

If you run fixparts it should detect the backup gpt info and offer to remove it:
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by westie457 on 2012-02-12
Well some good news. your partitions are still there and everything is still intact and no sign of Ubuntu being installed.

Does your Windows still boot? If not we will fix that first. I t is more important than installing another OS at the moment.

If your windows is able to start tap repeatedly on F8 while the bios is doing the POST (power on self tests) and before the Windows logo appears to enter the recovery environment.

Choose repair my computer answer any questions that pop up and then select Start up Repair. Run this at least twice, it does not repair everything on the first attempt, until you get a message that says 'Repairs completed successfully.



If you get the message 'Windows cannot automatically repair this system' report back here giving as much information as you can.

I am now going to start researching for possible solutions.


===========================================================

A better solution has been posted by darkod. Go with that.

---

### Post by nimraynn on 2012-02-12
> **darkod said:**
> The message that GPT table was detected means there is some remaining of GPT table. Because according to the fdisk results your partitions are msdos.
What probably happened is that the disk came with gpt table, but you changed it to msdos. When you do that in windows, it seems it changed the partition table, but in fact doesn't delete the backup gpt table (which all gpt disks have).

So for linux, it creates confusion whether the disk is msdos or gpt because it sees both tables, the main one, and the undeleted gpt backup.

And in case it can't see things correctly, Gparted doesn't show any partitions for your protection, because it can't see what is what.

If you run fixparts it should detect the backup gpt info and offer to remove it:
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Thank you for the great explanation and the link to fixparts. I've run fixparts and as you suggested, it offered to remove the backup GPT info. I hesitantly said yes (after making a backup of the partition table first of course ;)) and now gParted is able to see everything!

[img]http://www.nimraynn.co.uk/stuff/ubuntu3.png[/img]

I have now shutdown the Ubuntu LiveCD and booted back into Windows 7 before I even think about touching anything else and it appears to be all OK as well. It can still see everything without any issues at all :)

Thank you so much for your expert assistance :)

> **westie457 said:**
> Well some good news. your partitions are still there and everything is still intact and no sign of Ubuntu being installed.

Does your Windows still boot? If not we will fix that first. I t is more important than installing another OS at the moment.

If your windows is able to start tap repeatedly on F8 while the bios is doing the POST (power on self tests) and before the Windows logo appears to enter the recovery environment.

Choose repair my computer answer any questions that pop up and then select Start up Repair. Run this at least twice, it does not repair everything on the first attempt, until you get a message that says 'Repairs completed successfully.

If you get the message 'Windows cannot automatically repair this system' report back here giving as much information as you can.

I am now going to start researching for possible solutions.

Thank you for the advice. Windows was able to boot all along, no issues with that at all. I've followed through the advice given by darkod and it seems to now be all OK, so I'm going to attempt to do a Ubuntu installation again now and hopefully, all will be successful now! :)

---

### Post by darkod on 2012-02-12
Make sure you shrink the ntfs partition with windows Disk Management. Don't do it with the ubuntu install process.
First shrink in windows, leave the space as unpartitioned, restart few times in case windows wants to do disk checks.
Then boot with the ubuntu cd and install into the unpartitioned space.

---

