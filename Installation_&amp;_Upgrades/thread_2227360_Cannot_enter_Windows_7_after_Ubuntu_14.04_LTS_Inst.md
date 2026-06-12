---
title: "Cannot enter Windows 7 after Ubuntu 14.04 LTS Installation"
date: 2014-06-01
forum: Installation &amp; Upgrades
---

### Post by bobofdeath9 on 2014-06-01
Hello everyone,

I just finished installing Ubuntu 14.04 LTS on my Lenovo ThinkPad T420 and get a black screen when I try to boot windows from the grub menu. Using GParted I created an unformatted partition of 50GB and an unallocated partition of 50GB that came after the sda1 partition of 100GB. Initially the sda1 partition had 200GB allocated but only used ~80GB, and I shrank the partition to 100GB (probably a bad idea). During installation I selected the 'install ubuntu alongside windows' option, and everything worked fine. Once that finished I got to the grub menu and tried to enter windows but got sent back to the grub menu after a second or two of black screen. I then ran boot repair and it said it fixed the problem and got this boot-repair url: [http://paste.ubuntu.com/7566814/](http://paste.ubuntu.com/7566814/)

I followed this guide as close as I could, [http://lifehacker.com/5403100/dual-boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual-boot-windows-7-and-ubuntu-in-perfect-harmony), but deviated when it said to define a specific partition to use for ubuntu. It wouldn't let me pick a partition, saying that the root specified wasn't allowed. That's when I selected the install alongside windows option. 

Now when I try to boot Windows 7 it just goes to a black screen and stays there. I can enter Ubuntu fine and can access the data on the Windows partition.

---

### Post by Mark Phelps on 2014-06-01
Win7 provides a feature for making a free Repair CD -- but since it won't boot now, you can't use that.

Instead, you need to go to the site in the link, PURCHASE the repair ISO image, download it to a PC, burn it to CD, boot from it -- and run Startup Repair three times, that's right, three times: [http://neosmart.net/blog/2009/windows-7-system-repair-discs/]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

---

### Post by oldfred on 2014-06-01
Windows will not fix your problem. With grub installed to the PBR - partition boot sector your NTFS partition will not be seen by Windows. 
You have to use testdisk to restore the backup BS boot sector or PBR.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
If win7 use small 'system reserved' NTFS partition instead of the partition where windows was installed for win7
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)

OR essential the same instructions:
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)

---

### Post by bobofdeath9 on 2014-06-02
Hey thanks for the help. I got the testdisk and ran it up to the last screen. Mine says Boot Sector: OK, Backup Boot Sector: Bad. It gives me the option to 'Copy boot sector over backup boot sector'. Do I want to do that or find a Windows Machine and do the windows system recover? Would rebuilding the BS fix it?

---

### Post by oldfred on 2014-06-02
Then your only choice is to rebuild BS.
And then yo u have to run chkdsk from Windows. Windows should see it, but it is an XP type NTFS boot sector using ntldr and if you run chkdsk from a Windows 7 repair CD or flash drive then you can convert it to Windows Vista/7/8 type boot sector that uses bootmgr.

I think the Windows /fixBoot only does a restore.

If chkdsk then does not fix it, then you have to use bootsect.exe to create correct boot sector.
 How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
Use bootsect.exe to repair XP & older or Vista/7 bootsectors - Use diskpart, then list volumes to see which drive to use 
bootsect.exe /nt52 c:  *compatible* with operating systems older (XP) than Windows Vista.
bootsect.exe /nt60 c:  *compatible* with Windows Vista, Windows Server 2008 or later

Did you install grub to PBR more than once? Backup should have been good, but testdisk may think grub in PBR is ok as that can be valid. It just we almost never install grub2's boot loader to a PBR and never to Windows as that damages Windows.

---

### Post by bobofdeath9 on 2014-06-02
Oldfred, thanks for your quick replies. After running the Windows Recover disk 3 times, testdisk now says that both the Boot Sector and the Backup Boot Sector are OK, but booting windows from GRUB still gives me a blank black screen. 

I only installed grub once. I have grub2, as I updated grub from the command line inside Ubuntu.

---

### Post by oldfred on 2014-06-02
Running repair 3 times should work.
Perhaps another chkdsk?

Does Boot-Repair show it as a normal Windows 7 boot sector? It should as I do not think repairs would work otherwise.

---

### Post by bobofdeath9 on 2014-06-02
I tried running the repair 3 times. And then a chkdsk. The chkdsk didn't find any errors. I think maybe grub is installed twice, it has two entries at the top of [http://paste.ubuntu.com/7574444/](http://paste.ubuntu.com/7574444/). It says one is in sda and one in sdb. (Though I think the sdb is the external hard drive I have plugged in) The boot repair shows windows 7 as normal, but grub shows 'Windows 7 (Loader)'. 

I'm tempted to grab all the data from the hard drive and wipe it to re-install just ubuntu.

---

### Post by oldfred on 2014-06-02
Boot-Repair installs grub2's boot loader to all drives, but the external drives ones, if you tell it sdb is an external drive.
 
Your Windows partition looks normal now. Not sure then why Windows would not work?

---

### Post by bobofdeath9 on 2014-06-02
Would it have something to do with shrinking the partition size for the windows partition? It is the ntfs partition, and I shrunk it before creating the ubuntu partition. I used gparted.

---

### Post by oldfred on 2014-06-02
Sometimes that can be an issue. Windows has to run chkdsk after any resize and best to use Windows to shrink the NTFS partition, but never to create new partitions.

But many say they have used gparted without issue. Windows still has to run chkdsk to update its size. And that should fix any resize issues. Did you shrink it too much? Windows really likes to have 30% free space.

---

### Post by bobofdeath9 on 2014-06-05
Hey oldfred. I think the shrinking with gparted may have been the problem. It's not that big of a deal not being able to get back into windows, especially since I found wine and can get to all my data and programs on the 'windows' partition with wine. I used clonezilla to clone that part of the hard drive and am going to reinstall windows on it so that I can actually dual boot, but it doesn't really matter if I don't. Thanks for trying to help so much. 

If anyone else finds this problem and reads to the bottom of the thread, I think the takeaways are:

Use Windows to defragment then shrink the windows partition then straight away run the chkdsk from the repair cd to reset the boot sector. I have Windows 7 so this may not apply to Windows 8.

Then you should be able to intstall Ubuntu alongside windows and dual boot to your hearts content.

---

