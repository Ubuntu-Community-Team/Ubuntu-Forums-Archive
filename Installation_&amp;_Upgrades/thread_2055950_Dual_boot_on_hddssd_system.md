---
title: "Dual boot on hdd/ssd system"
date: 2012-09-10
forum: Installation &amp; Upgrades
---

### Post by Karyn on 2012-09-10
Some people have already posted about this problem, but I'm a bit scared of messing with my new computer, so I'm posting my own thread.

I want to install Ubuntu 12.04 as a dual boot with Win 7 on my new Dell Inspiron 14z laptop. It has a 32 GB ssd and a 500 GB hdd. I will mostly be using Ubuntu, but I still want to keep Windows as a security if I should run into something that doesn't like Linux.

When I try installing from the LiveCD I get these exact screens [http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121) and I'm fairly sure that the partitions are the same too. In windows I can see that the hdd has three partitions (OEM-partition 39 MB, recovery 16GB and C: 450 GB) and that the ssd has one (Hibernation(?) 8 GB).

As far as I can understand from these threads I should be able to deactivate the ISRT and RAID and thus free the ssd and be able to install Ubuntu. I'm not satisfied with how they solve the dual boot, though.
[http://ubuntuforums.org/showthread.php?t=2050413](http://ubuntuforums.org/showthread.php?t=2050413) 
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204) 
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155) 


What I would like to do is this:
Place / and /swap on the ssd (sdb) by removing the partition that's already there.
Place /home on the hdd (sda) by shrinking the C:-partition.

Should I place the boot-loader somewhere special or can I just let the boot-repair take care of that afterwards?

Do you think that this will work without messing up the Windows installation (too much)? Is there anything else that I need to consider?

---

### Post by oldfred on 2012-09-10
The combination of Windows & vendor almost always use all 4 primary partitions. You may not be seeing the hidden 100MB boot/repair Windows partition.

Best to fully backup Windows & make a Windows repairCD or USB first.

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. 
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)

If like the other Intel Smart Response and not just the Windows Hiber file, then you may have to remove RAID settings. If just the hivernation file you may want to recreate that in the c: partition.

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings

Shrink Windows with the Windows MMC partition tools but do not create any new partitions with Windows.

Install to external drive 11.04. Also any second drive.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. 
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail - now alternative (text based) installer
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

Herman also has a page on USB flash or SSD install.
It does not have to be encrypted BIOS based system:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory Installation using alternative text based installer
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
More discussion Dec 2010, more SSD info
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)
[http://ubuntuforums.org/showthread.php?t=1404664](http://ubuntuforums.org/showthread.php?t=1404664)

---

### Post by Stephan H on 2012-09-10
Hello,

Can I just add another question here:

I'm trying to do the same, got W7 installed on a single 250GB HDD partition which is completely in NTFS so will need to make a partition in W7 first, then install (K)Ubuntu and re-format the free partitions if I understand this correctly ([http://tiny.cc/2clfkw](http://tiny.cc/2clfkw)).

But in addition I would like to create a partition that can be accessed through both systems so that one can e.g. open PDF files from W7 as well as (K)Ubuntu. Thinking of using ext4 for this and use a "Linux Reader" when working under W7. Would that work?

---

### Post by Mark Phelps on 2012-09-10
> **Stephan H said:**
> Hello,

Can I just add another question here:

I'm trying to do the same, got W7 installed on a single 250GB HDD partition which is completely in NTFS so will need to make a partition in W7 first, then install (K)Ubuntu and re-format the free partitions if I understand this correctly ([http://tiny.cc/2clfkw](http://tiny.cc/2clfkw)).
If you have to shrink the W7 partition to make room, do NOT use GParted or the Ubuntu installer; instead, use the Win7 Disk Management utility.  It will give you less flexibility, but you won't run the risk of corrupting the Win7 boot process.

> But in addition I would like to create a partition that can be accessed through both systems so that one can e.g. open PDF files from W7 as well as (K)Ubuntu. Thinking of using ext4 for this and use a "Linux Reader" when working under W7. Would that work?
Both MS Windows and Linux can read/write NTFS partitions.  I would trust that before I would trust the "Linux Reader" working under Win7.

---

### Post by Karyn on 2012-09-11
Thanks for all the info. I'm not sure if I'm more or less confused now, though.

I think that the Dell system might be different from the HP one, since I can't access the recovery partition as a volume in the explorer (but that might also be because I'm not used to finding hidden things in Windows).

For now I will try these steps.

1. Shrink the C: partition on the hdd in Windows.
2. Make a new recovery CD.
3. Make an image of the recovery partition.
4. Deactivate the accelration in the IRST.
5. Change from RAID to AHCI in the BIOS.
6. Try installing Ubuntu. If it doesn't work I will try to remove the recovery partition.

---

### Post by oldfred on 2012-09-11
You will probably have to remove the RAID meta-data or old RAID settings as posted above.

I had this in my notes, not sure if it still applies to your newer system.
Dell restore partition.
[http://www.goodells.net/dellrestore/](http://www.goodells.net/dellrestore/)

---

### Post by YannBuntu on 2012-09-11
Hi

> **Karyn said:**
> For now I will try these steps.

1. Shrink the C: partition on the hdd in Windows.
2. Make a new recovery CD.
3. Make an image of the recovery partition.
4. Deactivate the accelration in the IRST.
5. Change from RAID to AHCI in the BIOS.
6. Try installing Ubuntu. If it doesn't work I will try to remove the recovery partition.

Before all, please indicate your [Boot-Info]("https://help.ubuntu.com/community/Boot-Info") URL, so that we know your initial configuration.

---

### Post by Karyn on 2012-09-12
The boot-info URL: [http://paste.ubuntu.com/1200154/](http://paste.ubuntu.com/1200154/)

(Running boot-repair was a bit funny because the text in the program wasn't showing. The only thing on the buttons was (), but since I had the home-page open on my other computer it didn't matter very much. Just a bit strange.)

I will read the page about the Dell restore partition, maybe there's something still the same.

Edit: I think this applies to my computer, except there's no MediaDirect button: [http://www.goodells.net/dellrestore/vista/](http://www.goodells.net/dellrestore/vista/)

---

### Post by YannBuntu on 2012-09-12
(concerning the blank windows: [http://ubuntuforums.org/showpost.php?p=12233792&postcount=529](http://ubuntuforums.org/showpost.php?p=12233792&postcount=529))

Your Boot-Info is ok anyway.

---

