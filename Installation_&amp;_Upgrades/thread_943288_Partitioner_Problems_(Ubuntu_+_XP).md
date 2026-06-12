---
title: "Partitioner Problems (Ubuntu + XP)"
date: 2008-10-10
forum: Installation &amp; Upgrades
---

### Post by EdwardFisher on 2008-10-10
Hello everyone.
Im looking to dual boot my desktop machine with linux and XP. 
I have been trying to go up the learning curve for installing linux.

XP install
Create 3 partitions on 500Gb Raid 0 - stripe HD (2 x 250Gb)
The three partitions are:
C:/   250Gb  (Windows - XP)
D:/   100Gb  (Linux - Ubuntu)
E:/   150Gb  (General Docs)
XP is installed in partition C:/ and gives no problems on install
I then formatted partition D:/ with NTFS format.
I then reboot the computer to install Ubuntu direct from CD.

My problem is that when the Ubuntu installer comes to open up the partitioner (manual mode) it does not recognise that the two HDs are in Raid0 format and insists on two HDs.
 
Also the partitioner does not seem to recognise that the HDs have already been partitioned. It does not show C, D, and E as partitioned above.

I would simply like to install Ubuntu into partition D without damaging XP.

Thanks.
Ed (linux newbie)

N.B. I have tried using the guided partitioner but as it formats some sections of the disk when i reboot after install i get a GRUB 2 Error and cant boot either XP or Ubuntu.
Exactly the same happens if i try to use manual partition and set up a new partition table (it does and formats those partitions again (Unable to deselect format)!!

---

### Post by caljohnsmith on 2008-10-10
> **EdwardFisher said:**
> 
XP install
Create 3 partitions on 500Gb Raid 0 - stripe HD (2 x 250Gb)
The three partitions are:
C:/   250Gb  (Windows - XP)
[COLOR="Red"]D:/   100Gb  (Linux - Ubuntu)[/COLOR]
E:/   150Gb  (General Docs)
XP is installed in partition C:/ and gives no problems on install
[COLOR="Red"]I then formatted partition D:/ with NTFS format[/COLOR].
I then reboot the computer to install Ubuntu direct from CD.

I can't help you with your RAID issues, but I thought I would at least mention that Ubuntu can't use NTFS for its file system; you'll need to use ext3 or some other linux file system for Ubuntu. Did you maybe format it temporarily to NTFS in Windows with the intention of changing it later? I just want to make sure that issue doesn't hold you up. :)

---

### Post by EdwardFisher on 2008-10-10
Perhaps the NTFS format that i did in windows is the reason why it wont detect the partition in the ubuntu installer. 
There wasnt an option for ext3 when i formatted the partition from windows, but i guess the ubuntu installer does that anyway as long as it can find the partitions.
Cheers
Ed

---

### Post by sturdyworks on 2008-10-11
I am also struggling to understand these RAID install issues tonight. Just want to add Ubuntu dual-boot to my Dell XPS 2010 running Vista Ultimate.

Dell installed Vista on 2x200GB SATA drives in RAID-0. The SATA HD & RAID controller chipset is by Intel.

When I select to the "manual partition step" in Ubuntu install it simply shows two 200GB drives to choose from. This obviously means it is not automagically detecting my RAID setup.

Vista has a new Computer -> Manage -> Disk Management application that shows this partitioning:

--------------------------------------------------------------
|        |         | D:      | C:    |             |         |
| Disk 0 | 64MB    | 10GB    | 280GB | 80GB        | 2GB     |
|        | EISA    | NTFS    | NTFS  |             |         |
|        | Config. | Primary | Boot  | Unallocated | Primary |
--------------------------------------------------------------

I created the "80GB Unallocated" for Ubuntu tonight by selecting C: partition, right mouse click, then select Shrink Partition...

There is not another "Disk 1" type on listing, so we must assume that everyone of my partitions are on the RAID-0 setup.

I am an experienced open source programmer, but must admit I have relied heavily on my Systems Administrators in the past, so I'm more than a bit worried about destroying Vista.

There is a RAID related artical on the Ubuntu site:
[https://help.ubuntu.com/community/Installation/LVMOnRaid](https://help.ubuntu.com/community/Installation/LVMOnRaid)
It mentions things like "Make it a RAID partition, Mark it as bootable, Choose the Configure RAID option" but that guy was doing some truly wacky stuff in his "Installing over an Existing RAID Array" ramblings.

I wish I knew the point, during the Ubuntu install, when the disks and boot records and such will actually get modified--them I would be more likely to tinker around a bit. I do not want to loose Vista tonight--Got work to do...

B.A.S

---

### Post by sturdyworks on 2008-10-11
I am also struggling to understand these RAID install issues tonight. Just want to add Ubuntu dual-boot to my Dell XPS 2010 running Vista Ultimate.

Dell installed Vista on 2x200GB SATA drives in RAID-0. The SATA HD & RAID controller chipset is by Intel.

When I select to the "manual partition step" in Ubuntu install it simply shows two 200GB drives to choose from. This obviously means it is not automagically detecting my RAID setup.

Vista has a new Computer -> Manage -> Disk Management application that shows this partitioning:

--------------------------------------------------------------
|        |         | D:      | C:    |             |         |
| Disk 0 | 64MB    | 10GB    | 280GB | 80GB        | 2GB     |
|        | EISA    | NTFS    | NTFS  |             |         |
|        | Config. | Primary | Boot  | Unallocated | Primary |
--------------------------------------------------------------

I created the "80GB Unallocated" for Ubuntu tonight by selecting C: partition, right mouse click, then select Shrink Partition...

There is not another "Disk 1" type on listing, so we must assume that everyone of my partitions are on the RAID-0 setup.

I am an experienced open source programmer, but must admit I have relied heavily on my Systems Administrators in the past, so I'm more than a bit worried about destroying Vista.

There is a RAID related artical on the Ubuntu site:
[https://help.ubuntu.com/community/Installation/LVMOnRaid](https://help.ubuntu.com/community/Installation/LVMOnRaid)
It mentions things like "Make it a RAID partition, Mark it as bootable, Choose the Configure RAID option" but that guy was doing some truly wacky stuff in his "Installing over an Existing RAID Array" ramblings.

I wish I knew the point, during the Ubuntu install, when the disks and boot records and such will actually get modified--them I would be more likely to tinker around a bit. I do not want to loose Vista tonight--Got work to do...

B.A.S

---

### Post by EdwardFisher on 2008-12-10
Hey Guys. 
I'm still having problems with this (I gave up for a while). 
Anyone have any ideas on how to get it to recognise that the two disks are in raid0 configuration? I don't know enough about the raid drivers or config to sort that stuff out.

Cheers

---

