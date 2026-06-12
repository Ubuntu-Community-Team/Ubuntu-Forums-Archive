---
title: "Trouble installing lubuntu alongside Windows XP"
date: 2013-06-30
forum: Installation &amp; Upgrades
---

### Post by uncoordinated on 2013-06-30
My computer has a 1TB HDD that had one big NTFS partition for Windows. I have managed to [shrink]("http://imgur.com/tXn1DuB") that partition in half in gparted in the live session of lubuntu that I am running so have of the space is unallocated. I was following a guide to installing lubuntu alongside windows and in one of the steps you pick if you want to install alongside windows, over windows, or do something else for some reason mine skipped that step and goes straight to [this.]("http://imgur.com/NEkzYzT") 

How should I proceed? I would like to install lubuntu in the unallocated space that I created.

---

### Post by sudodus on 2013-06-30
Welcome to the Ubuntu Forums :-)

Things can be misunderstood or go wrong. Editing partitions and installing operating systems is risky, so ***you should backup your Windows*** before going ahead. Just in case.

-o-

Did you only shrink the partition, or did you also create any new partitions? In other words, is there still a big unallocated space on your HDD?

In that case the installer finds it and assumes that it should install Lubuntu there (creating a root partition and a swap partition).

Furthermore, if you have only one internal drive, the bootloader should be installed into the head of it (/dev/sda), which is indicated in the linked picture, so it is OK.

---

### Post by uncoordinated on 2013-06-30
Ya I shrunk the partition and there is a big unallocated space on my HDD. When I try and press install thought it says, "No root file system is defined. Please correct this from the partitioning menu"? What should I do?

---

### Post by Bashing-om on 2013-06-30
uncoordinated; Hi !

Are you setting up your partitions manually ? If so .. best my poor memory recalls .. 
In that "partitioning menu" press change (lower left)->formatting page; format set to ext4 (my suggestion), and the "use as" of the partition as / (only the '/' slash character as that character means "root"; verify the size and you may give the partition a label  - root - type literally here the word root./// A sticky point ... how many partitions are set up on this hard drive ? In the older partitioning scheme one can only have 4 partitions max... if three are taken up by Windows .. then the partition to hold ubuntu must be made as an extented partition consuming the unallocated space ... then within this extended 4th partition one may make as may "logical" partitions as one needs or wants. The partitions / and swap as a minimum. So if that extended partition is in existence as that 4th partition .. then both / and swap are created within that extended partition as "logical" partitions. Set the type field as logical for both / and swap ....for the swap partition set the format to "swap".
Make sure all the above is set and continue installation... the installer should now be happy.

I do not recall if one has the option "install along side of" another operating system with the lubuntu installer ... I have always set up my partitions in GParted first and installed "manually" and just never paid much attention to other install options. 

The above procedure has worked several times for me. I hope it it clear and correct enough to get you over this spot.
[INDENT][INDENT]
[INDENT][INDENT][INDENT][INDENT]I be try'n to help[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by uncoordinated on 2013-06-30
> **Bashing-om said:**
> uncoordinated; Hi !

Are you setting up your partitions manually ? If so .. best my poor memory recalls .. 
In that "partitioning menu" press change (lower left)->formatting page; format set to ext4 (my suggestion), and the "use as" of the partition as / (only the '/' slash character as that character means "root"; verify the size and you may give the partition a label  - root - type literally here the word root./// A sticky point ... how many partitions are set up on this hard drive ? In the older partitioning scheme one can only have 4 partitions max... if three are taken up by Windows .. then the partition to hold ubuntu must be made as an extented partition consuming the unallocated space ... then within this extended 4th partition one may make as may "logical" partitions as one needs or wants. The partitions / and swap as a minimum. So if that extended partition is in existence as that 4th partition .. then both / and swap are created within that extended partition as "logical" partitions. Set the type field as logical for both / and swap ....for the swap partition set the format to "swap".
Make sure all the above is set and continue installation... the installer should now be happy.

I do not recall if one has the option "install along side of" another operating system with the lubuntu installer ... I have always set up my partitions in GParted first and installed "manually" and just never paid much attention to other install options. 

The above procedure has worked several times for me. I hope it it clear and correct enough to get you over this spot.[INDENT][INDENT][INDENT][INDENT][INDENT][INDENT]I be try'n to help[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]

I would like to do the partitioning just the easy way, but it skips the step where I can choose to install alongside windows and goes to the custom option(i think). It is really annoying and I just want to do it the easy way :(

---

### Post by sudodus on 2013-06-30
If you do it like this, we can be sure it will work:

1. Start gparted again and create an extended partition using all unallocated space.

2. Create a swap partiton of slightly more than your RAM if you plan to hibernate. Otherwise you can have less swap than RAM, but I suggest at least 1 GB anyway.

3. Use the rest of the space (in the extended partition) for an ext4 partition.

4. Start the installer again and at the partitioning page, select 'Something else' which means manual partitioning.

5. Select the new ext4 partition to be used as / (root partition).

6. Check that the bootloader will will be installed to /dev/sda (the head of sda, only letters no digit)

7. Swap will be selected automatically, so now you can continue from the partitioning page ...

This should work if you have at least 768 MB RAM. Otherwise you might need to start the installer directly from the boot menu (or change to the alternate iso file).

Good luck :-)

---

### Post by Mystic38 on 2013-07-01
I have recently done this. I shrank my windows partition by 100GB, restarted windows to confirm it was all ok, put in the live CD, booted into ubuntu then hit install.

The selection "install alongside windows" will automatically pick that unused partition and install ubuntu there..iirc you may need to confirm that specific partition in the setup prompts, but this will give you a dual boot machine, so  give you a boot choice of ubuntu/windows 7 without any detailed involvement on your part.

none of the above conflicts with the extra technical detail given above..thats all recommended good stuff, just not *required*...

> **uncoordinated said:**
> My computer has a 1TB HDD that had one big NTFS partition for Windows. I have managed to [shrink]("http://imgur.com/tXn1DuB") that partition in half in gparted in the live session of lubuntu that I am running so have of the space is unallocated. I was following a guide to installing lubuntu alongside windows and in one of the steps you pick if you want to install alongside windows, over windows, or do something else for some reason mine skipped that step and goes straight to [this.]("http://imgur.com/NEkzYzT") 

How should I proceed? I would like to install lubuntu in the unallocated space that I created.

---

### Post by uncoordinated on 2013-07-01
The only thing is that it won't let me click install alongside windows so I'm just going to follow sudodus' steps and see what happens.

---

### Post by uncoordinated on 2013-07-01
OK I'm just going to write what I did so if anything happens you guys canfigure out what I did incorrectly because I am fairly new to this.

1. Created extended partition with all the unallocated space. 

2. Created Logical Partition with File System as "linux-swap" with 1 mb of free space preceding, a new size of 2.5Gb(I have 2 gb of ram) and a following free space of 474432Mb. 

3. Created Logical Partition with File System of ext4 with rest of unallocated space with 1mb of free space preceding. 

4. So I went throught the installer and it skipped the page where you chose install alongside windows or over it AGAIN anth it went to this page [http://imgur.com/NEkzYzT](http://imgur.com/NEkzYzT). It is sooo frustrating I try and press the plus button or minus button or even the change button and it just crashes. 

I should have said it earlier, but it gives me these errors when I go into gparted, but I was able to just press cancel 3 times so I didn't worry about them. Now I have a feeling it must be related to my problems. 

Could not stat device /dev/mapper/ddf1: virtual drives with CRC  449B3D65, expected 887D7C20 on /dev/sda - No such file or directory.
Could not stat device /dev/mapper/ddf1: physical drives with CRC  97FA6A4A, expected B97A44DD on /dev/sda - No such file or directory.
Could not stat device /dev/mapper/ddf1: VD CFG with CRC 681D7C6F, expected 9D459FFD on /dev/sda - No such file or directory.

---

### Post by oldfred on 2013-07-01
/dev/mapper/ddf1 is either RAID or LVM.

Are you installing with encryption as that uses LVM?
Are you using BIOS RAID with Windows?
Are you not using RAID but drive was RAID before? Then you can remove RAID meta-data from drive.

Standard desktop installer does not include RAID. Older versions alternative installer or server installer have RAID as an option.

---

### Post by uncoordinated on 2013-07-01
I don't think I'm installing with encryption the uses LVM(I have no idea what that is)
I only have one hard drive so I don't think I'm using BIOS RAID or whatever. 
I have no idea if the drive was using raid before, but I think it was reformatted recently. 

I just got the installer from the proper website and just burned it on a CD.

---

### Post by sudodus on 2013-07-01
> **uncoordinated said:**
> OK I'm just going to write what I did so if anything happens you guys canfigure out what I did incorrectly because I am fairly new to this.

1. Created extended partition with all the unallocated space. 

2. Created Logical Partition with File System as "linux-swap" with 1 mb of free space preceding, a new size of 2.5Gb(I have 2 gb of ram) and a following free space of 474432Mb. 

3. Created Logical Partition with File System of ext4 with rest of unallocated space with 1mb of free space preceding. 

4. So I went throught the installer and it skipped the page where you chose install alongside windows or over it AGAIN anth it went to this page [http://imgur.com/NEkzYzT](http://imgur.com/NEkzYzT). It is sooo frustrating I try and press the plus button or minus button or even the change button and it just crashes. 

I should have said it earlier, but it gives me these errors when I go into gparted, but I was able to just press cancel 3 times so I didn't worry about them. Now I have a feeling it must be related to my problems. 

Could not stat device /dev/mapper/ddf1: virtual drives with CRC  449B3D65, expected 887D7C20 on /dev/sda - No such file or directory.
Could not stat device /dev/mapper/ddf1: physical drives with CRC  97FA6A4A, expected B97A44DD on /dev/sda - No such file or directory.
Could not stat device /dev/mapper/ddf1: VD CFG with CRC 681D7C6F, expected 9D459FFD on /dev/sda - No such file or directory.
I think you did what you should in those steps. There is some other problem.
 
- Have you checked that the download was successful (with md5sum)?
- Did you check the disk?

An alternative might be to download and use the alternate installer.

- Which version 12.04, 12.10, 13.04 or 13.10 are you trying to install?
- And is it 32-bit (i686) or 64-bit amd64?

If you are trying 13.10, you must remember that it is still in alpha testing stage, and will not be ready for normal use until October.

---

### Post by uncoordinated on 2013-07-01
I don't think I'm installing with encryption the uses LVM(I have no idea what that is)
I only have one hard drive so I don't think I'm using BIOS RAID or whatever. 
I have no idea if the drive was using raid before, but I think it was reformatted recently. 

I just got the installer from the proper website and just burned it on a CD.

---

### Post by uncoordinated on 2013-07-01
Ops posted twice I don't know how to delete them

---

### Post by oldfred on 2013-07-01
If you are not running RAID, you need to remove RAID meta-data from drive.

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discussion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

---

### Post by uncoordinated on 2013-07-01
So I ran the command in terminal and I get ERROR: ddf1:seeking device "/dev/sda" to 512104901378028, ERROR: writing metadata to /dev/sda, offset ##########(really long number) sectors, size 0 bytes returned 0, ERROR: erasing ondisk metadata on /dev/sda

Im going to check BIOS now.

---

### Post by uncoordinated on 2013-07-01
The BIOS says that the SATA operation is set on "RAID Autodetect / ATA" and the only other option is "RAID ON"

---

### Post by uncoordinated on 2013-07-01
The command "apt-get purge dmraid" worked will follow up.

---

### Post by uncoordinated on 2013-07-01
It worked! By deleting the metadata for RAID it finally was able to install properly! 
Thanks Guys.

---

### Post by Bashing-om on 2013-07-01
uncoordinated; Hey Great !

Great help is but a keyboard away !

[INDENT][INDENT]doing it together, gets done
[/INDENT][/INDENT]

---

