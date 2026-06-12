---
title: "Ubuntu installer unable to read partition table (10.04)"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by Mohammad_Khalid_Hussain on 2010-05-01
Hi there,

I'm trying to install Ubuntu Linux 10.04 on my computer with following specs:

ASUS P5KR Mobo
HIS 2600XT GFX
160 GB Hitachi Harddisk (SATA)
500 GB Hitachi Harddisk (SATA) - Only for Data.

The 160 GB Harddisk is currently split into 3 main partitions:
i) 200 MB created by Win7 setup.
1) Windows 7 
2) Leopard OSX
3) Partition formatted in Leopard as Journal which is empty, meaning I can convert this if I want and onto which I will install Ubuntu.

My problem is that despite booting up fine, installer starting and working fine, it cannot however detect my partition table, it thinks its unallocated.

The funny thing is that I can mount the partitions and view the data but the installer however can't see it.

Patiently seeking advice as to how to solve this.
Screenshot included.

Thanks for your time.
[[IMG]http://img688.imageshack.us/img688/8140/screenshotiz.th.png[/IMG]](http://img688.imageshack.us/i/screenshotiz.png/)

---

### Post by tommcd on 2010-05-01
It may be that you are having this problem that was mentioned in the Ubuntu 10.04 release notes:
[http://www.ubuntu.com/getubuntu/releasenotes/1004#Partition%20alignment%20changes%20may%20break%20some%20systems](http://www.ubuntu.com/getubuntu/releasenotes/1004#Partition%20alignment%20changes%20may%20break%20some%20systems)
Your motherboard is not the same chipset as those Asus motherboards mentioned in the release notes though. However, to rule out that problem, I would try adding the **partman/alignment=cylinder**  boot parameter when starting the installer, as it says on the link I posted.
Hope this helps.

---

### Post by Mohammad_Khalid_Hussain on 2010-05-02
I need a little help with this. Where do I type it? The CD boots and enters the desktop of the LiveCD, I'm new to this , please help me out.

Some things I tried:
1) Typed that in Terminal along with the 'sudo' command. Told me there is no such file or directory.
2) Typed 'partman /alignment=cylinder' in Terminal and got 2 lines saying something before a partition manager opened in the terminal itself which could not read the partition table either.
3) Changed SATA type from IDE Enhanced to AHCI. No difference.
4) Changed SATA type from IDE Enhanced to IDE Compatible. No difference.

Any other ideas?

Thanks for the help so far :)

---

### Post by tommcd on 2010-05-03
> **Mohammad_Khalid_Hussain said:**
> I need a little help with this. Where do I type it? The CD boots and enters the desktop of the LiveCD, I'm new to this , please help me out.

When the live CD boots to the main menu, where it gives you the option to run Ubuntu without making changes to your computer, or to install Ubuntu, etc. ...
Just fit the **F6** key. This will give you a list of alternative boot options. Since the option **partman/alignment=cylinder** will probably not be listed there as one of the options, you will need to enter it manually.
To do this, simply hit the **Esc** key. Then leave a space following the "--" and add the desired option: (partman/alignment=cylinder).
Reference:
[https://help.ubuntu.com/community/BootOptions#Changing%20the%20Boot%20Option%20Configuration%20Line](https://help.ubuntu.com/community/BootOptions#Changing%20the%20Boot%20Option%20Configuration%20Line)
And for a comprehensive list of other boot options available for Ubuntu:
[https://help.ubuntu.com/community/BootOptions#Common%20Boot%20Options](https://help.ubuntu.com/community/BootOptions#Common%20Boot%20Options)

Also, when you first boot the Ubuntu live CD, did you first choose the option "Check CD for Defects" and let that run to insure the CD is good??
This is *very* important. You should first verify that your install Cd is valid before proceeding with more complicated maneuvers.
Your motherboard has the Intel P35 Northbridge/iCH9R Southbridge Chipset:
[http://www.ozhardware.com.au/Motherboard-Reviews/ASUS-P5KR-Motherboard-Review.html](http://www.ozhardware.com.au/Motherboard-Reviews/ASUS-P5KR-Motherboard-Review.html)
This chipset is well supported in linux. 
Write back if you need more help. We will get your Ubuntu installed one way or the other!!

---

### Post by Mohammad_Khalid_Hussain on 2010-05-04
Tried the method, adding the 'partman/alignment=cylinder' string to boot and it still can't detect any operating systems on the disk or the partition table.

Checked the CD for errors and it says that no errors were found.

Maybe its not an alignment problem?

---

### Post by Mohammad_Khalid_Hussain on 2010-05-04
Some extra information:
1) For the 160GB harddisk, GParted says that it can't have overlapping partitions.
2) For the 500GB harddisk, GParted says that it can't have a partition outside disk.

Any idea how to solve these errors?

---

### Post by antiram on 2010-05-04
you could try testdisk to repair the partition tables.

or repair it by hand with fdisk -u, but this is risky.
eg. delete partition sdb1 and make a new primary partition with start sector 2048 end sector 976773168 (or 976773167), save.
delete partition sda1 and make a new primary partition (and bootflag for win) with start sector 2048 end sector 81930239, save. 
then reboot.

edit: and DON'T FORMAT the partitions after manual repair, the problem is only the partition table, which is located ONLY in the first sector of a disk, 3-4 bytes are wrong here.

---

### Post by tommcd on 2010-05-04
> **Mohammad_Khalid_Hussain said:**
> Some extra information:
1) For the 160GB harddisk, GParted says that it can't have overlapping partitions.
This would seem to indicate that something is not right with your partitions. Can you run the Ubuntu live CD, open a terminal, and run:
```
sudo fdisk -l
```
and post the output here. Fdisk will list all your partitions, as well as where they start and end.
> **Mohammad_Khalid_Hussain said:**
> 
Any idea how to solve these errors?
I would try burning a Parted Magic live CD:
[http://partedmagic.com/](http://partedmagic.com/)
Boot from the Parted Magic live CD and delete partition #3 on the 160GB disk that you said you wanted to install Ubuntu on in your first post. Deleting the partition will create unallocated space. Then, using Parted Magic, try to format this space to an ext4 file system. Then boot up the Ubuntu CD and try to install Ubuntu onto this ext4 file system.
Or, after deleting partition #3, just try booting up the Ubuntu CD and try to install Ubuntu to the free space.
I'm not sure what else you could try.

---

### Post by antiram on 2010-05-04
the problem is that sda1 overlaps sda2 and sdb1 last sector is bigger than max sector of sdb

---

### Post by psusi on 2010-05-04
> **antiram said:**
> the problem is that sda1 overlaps sda2 and sdb1 last sector is bigger than max sector of sdb

Yep, your partition table is corrupt.  Back up your data and reformat.

---

### Post by Mohammad_Khalid_Hussain on 2010-05-04
> you could try testdisk to repair the partition tables.

or repair it by hand with fdisk -u, but this is risky.
Could you please elaborate on how to use testdisk?

> This would seem to indicate that something is not right with your partitions. Can you run the Ubuntu live CD, open a terminal, and run:
I believe this is provided in the first screenshot. But please do correct me if I'm wrong.

---

### Post by antiram on 2010-05-04
install package testdisk
run testdisk from terminal as root
select new from [with new log|append log|no log] 
select disk sda or sdb
select partition style intel/pc
select analyse from [analyse|advanced|geometry|options|mbr code|delete|quit]
>>>edit:also select options here to set "cylinder boundary:no"<<<
it asks then "search for vista partitions", i said no
then testdisk found my
2 linux partitions ext3
1 hfs partition (formatted with linux mkfs.hfsplus)
1 linux swap

but my big btrfs partition was not found.
my testdisk run found nothing for repair.

---

### Post by Mohammad_Khalid_Hussain on 2010-05-05
Okay, I used testdisk for Windows since this was an easier choice for me. I did upto the search for Vista partitions part and after that I was presented with a list of partitions, some of which I recognized as old partitions I had wiped so I selected the current Windows partition I was using thinking it would fix it.

But it ended up wiping that partition out from the partition table and am now left with the 'No Operating System found.' message during bootup and can only see one empty partition from this disk in Ubuntu.

Is there a way I may be able to restore the Windows partition as it would be a hassle to reinstall everything?

Your advice is appreciated. Inform me if any extra information is required. Thanks :)

---

### Post by antiram on 2010-05-05
boot ubuntu livecd, fdisk -lu. You should see on sda
partition 1 sda1 startsector 2048 endsector 81930239 with bootflag (w7 boot)
partition 2 sda2 startsector 81930240 endsector 96266239 (osx)
(partition 3 sda3 startsector 96266240 endsector 188426239 (hfs empty))
on sdb
partition 1 sda1 startsector 2048 endsector 976773167 (w7)

if not then i would use fdisk -u to make this layout.

test if the data are ok:
mount /dev/sdb1 /mnt (should work)
ls /mnt
umount /dev/sdb1

make the w7 booting with w7 install cd. the old xp setup asks for repair twice before install. you should come to a console to do fixmbr, fixboot c:, fixbootmgr or so

then install linux on sda3. i dont know if the w7 repair is needed because ubuntu will install grub2 bootcode on sda.

---

### Post by Mohammad_Khalid_Hussain on 2010-05-05
Some advice as to how to perform the step correctly is required, please refer to following screenshot:

[IMG]http://img532.imageshack.us/img532/3155/screenshotng.th.png[/IMG]

Thanks for your time and efforts.

Regards,

---

### Post by antiram on 2010-05-05
what to do? the image is to small and not clickable

---

### Post by Mohammad_Khalid_Hussain on 2010-05-06
My mistake, :( , here it is:

[[IMG]http://img532.imageshack.us/img532/3155/screenshotng.th.png[/IMG]](http://img532.imageshack.us/i/screenshotng.png/)

---

### Post by antiram on 2010-05-06
the "Partition x does not end on cylinder boundary." is because Dos compatibility mode if fdisk. Use paramter -c for disabling, eg. fdisk -clu. Forget it, nobody needs the "Dos compatibility". In the near future the -c mode will be the default in linux fdisk and all new partitions are aligned to a multiple of 2048 sectors(1MB), like in w7.

"sudo mount /dev/sda2/mnt" needs a space before /mnt
```
sudo mount /dev/sda2 /mnt
```

"partition has different physical/logical endings":
Have you used different partition programs and/or different OS for this drive or fdisk -C -H -S parameters? Because its only 1GB, I would delete the sdc2 partition and make it new with the programs which you have used for the sdc1 partition.

---

### Post by dino99 on 2010-05-06
[http://ubuntuforums.org/showthread.php?t=1467891&page=2](http://ubuntuforums.org/showthread.php?t=1467891&page=2) post 14

---

### Post by Mohammad_Khalid_Hussain on 2010-05-06
Orite guys, I decided to just wipe the whole disk and start fresh. And after I'm set with Windows 7 and installing Lucid Lynx, we will worry about the second data partition. I mean I can read it and all but I would like to fix the partition table error.

---

