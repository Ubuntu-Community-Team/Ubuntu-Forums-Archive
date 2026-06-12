---
title: "Dualboot installation issues"
date: 2012-11-09
forum: Installation &amp; Upgrades
---

### Post by Calinou on 2012-11-09
**(see edit 3, the following paragraph is now quite invalid)**

I'm having partitioning issues with Xubuntu 12.10 64 bit. I reduced my Windows partition by 500GB. I now have a 1450GB Windows partition, 500GB unallocated, 50GB recovery partition and 1GB "OEM" partition.

I bet I shouldn't remove the recovery and OEM partitions, else my warranty could be voided (edit: not that important actually), or worse, computer could be unbootable.

I can't create new partitions in the unallocated space from the live CD's installer and gparted; the only automated partitioning options are "Replace Windows 7 with Xubuntu" and "Something else".

[edit] This is a computer with UEFI.

[edit 2] [http://ompldr.org/vZzd1ZA/Screenshot%20-%2011102012%20-%2010:30:21%20AM.png](http://ompldr.org/vZzd1ZA/Screenshot%20-%2011102012%20-%2010:30:21%20AM.png)

[B][edit 3] I might just end up removing all partitions and install Xubuntu -- I've used Linux for a long time and I don't think it is worth it because I'm not running any Windows-only software.
Here comes my two other questions:[/B]
1) Maybe -- since I'm not running any Windows-only software, should I attempt creating a new partition table and install Xubuntu instead? Will the computer be bootable if I do that?

2) I do play games on this computer (they do have native Linux versions) and I have a NVIDIA graphics card; the Arch Linux wiki says the proprietary NVIDIA driver cannot be used if using UEFI, is this true for Ubuntu and its derivatives?

---

### Post by ibjsb4 on 2012-11-09
UEFI ?

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=uefi&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=uefi&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F)

---

### Post by Calinou on 2012-11-09
Ah, forgot to mention, sorry. Yes, this is a computer with UEFI and GPT hard disk.

---

### Post by Mr_JMM on 2012-11-09
> **Calinou said:**
> the only automated partitioning options are "Replace Windows 7 with Xubuntu" and "Something else"

So what are your options with "Something else"? That is the option to manually select the partitions.

---

### Post by Calinou on 2012-11-09
> **Mr_JMM said:**
> So what are your options with "Something else"? That is the option to manually select the partitions.

I can create a new partition table, but that would destroy everything on the disk. I can also format one of the existing partitions, but that'd destroy data too. When I select the unallocated space, the "Create" button is grayed out.

---

### Post by oldfred on 2012-11-09
With gpt partitioning there is no issue on number of partitions. (ok some limit, 128 as default max). 

MBR partitioning has a 4 primary partition limit and then you have to convert one primary to the extended so you can add logicals, but all partitions in gpt are primary.

Are you using the 64 bit version of Ubuntu?

Boot into liveCD mode.
Post screenshot from gparted. And are there any little warning icons on any partitions. Click on them to see issue if you have any.

---

### Post by Calinou on 2012-11-09
Yes, 64 bit.

---

### Post by Calinou on 2012-11-10
Small bump, with a screenshot:
[http://ompldr.org/vZzd1ZA/Screenshot%20-%2011102012%20-%2010:30:21%20AM.png](http://ompldr.org/vZzd1ZA/Screenshot%20-%2011102012%20-%2010:30:21%20AM.png)

---

### Post by oldfred on 2012-11-10
You said it was gpt? 

With gpt you do not have primary & logical partitions, in effect they are all primary.

Your partition layout is typical of MBR(msdos) as your first partition is the hidden 100MB boot/repair partition for Windows not a fat32 efi partition. Windows has to use UEFI if gpt partitioning.

You have to backup either the vendor recovery (make DVD set) or utilities partition and delete one or both. Then you can create an extended partition and all the logical partitions you need.


Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. - gordintoronto
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)
Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)
The Hedge show graphically how to delete & create partitions:
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)

---

### Post by Calinou on 2012-11-10
This is a Medion computer, not HP. Thanks for the answer anyway. :)

---

### Post by oldfred on 2012-11-10
Does not really matter the brand, the configuration is just about identical for all Windows 7 computers.

---

### Post by Calinou on 2012-11-10
Another idea:
Maybe -- since I'm not running any Windows-only software, should I attempt creating a new partition table and install Xubuntu instead? Will the computer be bootable if I do that?

I do play games on this computer (they do have native Linux versions) and I have a NVIDIA graphics card; the Arch Linux wiki says the proprietary NVIDIA driver cannot be used if using UEFI, is this true for Ubuntu and its derivatives?

---

### Post by oldfred on 2012-11-10
There are issues with systems with dual video. But I thought you could still use bumblebee, but not sure if UEFI makes a difference or not.  

Dual Video Intel & nVidia
[http://ubuntuforums.org/showthread.php?t=1994622](http://ubuntuforums.org/showthread.php?t=1994622)

---

### Post by Calinou on 2012-11-15
"Solved" -- managed to remove Windows and install Xubuntu, it works fine. Thanks anyway.

---

