---
title: "Need info on installing on a different HD..."
date: 2009-11-19
forum: Installation &amp; Upgrades
---

### Post by weetoots on 2009-11-19
I have three HDs. 1.) Windoes 7 64bit installed.. 2.)used for backup files. 3.) an empty 40GB HD.

I want to install 9.10 32 bit on #3. It is currently formated as NTFS. 
In the installation process I got as far as which drive to install to, I picked /dev/sdc1 40024 MB, but got an error message "no root file system is defined. Please correct this from the partitioning menu". 
Do I re-format this drive to ext4?
Will 9.10 make the correct partitions it needs for installation?
By installing on a separate drive, as opposed to side-by-side, will I still get to dual boot in the MBR?

Thanks for your help.  

Al

---

### Post by Mze on 2009-11-19
reformat hard drive 3.

use ext 3 for now. Ext 4 has some bugs.

create a swap partition twice the size of your RAM.
create a root partition of about 10 gigs and use the rest for HOME

then Ubuntu should install just fine on that drive.

---

### Post by dvlchd3 on 2009-11-19
It sounds like you selected the manual option.  You can just select "Use entire drive" (or something like that) option, and choose the 3rd device.

Or if you perfer manual:

Select the 40GB NTFS partion, click "delete partition".
Click New partition, select SWAP, and set the size to about double the amount of physical memory you have.  (Double is usually best, but you can use less if you want...)
Click Ok.
Click New partition select ext4, the size should default to the remaining space on the drive.  Set the mountpoint to '/' (without quotes).
Click next.
All Done! :)

Hope this all helps.

---

### Post by Mze on 2009-11-19
You should get a dual-boot in the MBR.
From what I've read the MBR is installed in Harddrive 1 in 9.10, you don't get the option to choose.

see this [tutorial]("http://www.easy-ubuntu-linux.com/ubuntu-installation-606-9.html") for creating partitions on the harddrive

---

### Post by darkod on 2009-11-19
One thing that wasn't said is location for grub2 installation. With multiple drives you have to make up your mind what you want:
1. Install grub2 on the drive currently you are booting windows from (I guess drive 1). That way you don't need to change the boot drive order in bios.
2. Install grub2 where ubuntu will be, drive 3. That way don't be surprised if the computer keeps booting windows directly like you never installed ubuntu. You have to change the drive order in bios.

You can make this choice for grub2 when you install ubuntu, on the last screen. Before clicking Install click on Advanced, that will give you the option to select where grub2 should be. It is wise previously in the partitioner to remember which drive is called what by ubuntu, it won't necessarily be drives 1,2, 3 like you expect them to be, the order can be different.

---

### Post by weetoots on 2009-11-19
Thanks for the replies. I will install in the morning, after I get some sleep. Then I will not screw it up.

Al

---

### Post by EugeneS on 2009-11-19
Hi!

I have a condition which is similar to what you just described (darkod). I mean:
1. I have 2 hard drives installed.
2. On one of them I have Windows XP installed and running normally.
3. The second hard drive is divided to 3 partitions: NTFS partition, swap partition and ext3 partition.
4. I have Ubuntu installed on the ext3 partition of the second drive.
5. During the Ubuntu installation I choose to install the boot loader (GRUB) to the second drive.

So when I start the computer, Windows XP is booting correctly just as if I never had installed Ubuntu.
My problem is creating a dual boot menu.
What I tried to do is to extract the first 512 bytes from the second hard drive (which is supposedly the MBR), save it in a file, for example: bootsect.lnx and then create following reference in Windows boot.ini file:
c:\bootsect.lnx="Linux"

Now as a result - it didn't work for me.
When I done the above, I do get a windows boot menu which gives the "Linux" option but when I choose it I just get back to the same boot menu. So I can boot only Windows.

If I switch the hard drives in the BIOS menu I can't boot neither Windows XP nor Ubuntu. I mean if I choose Ubuntu, I get some GRUb error related to the missing system and if I choose Windows, I get the " Missing NTLDR" message. So I had to switch the hard drives back and continue with Windows only.


If someone could help me with this issue, I will be more than thankful!!

Thanks in advance.
Eugene

---

### Post by darkod on 2009-11-19
What version of ubuntu did you install and do you have grub or grub2?

---

### Post by EugeneS on 2009-11-19
Hi and thanks for the quick reply!

I have Ubuntu 9.04 and I don't remember at the moment what is the version of GRUB. By the way, how do I check it?


Thanks,
Eugene

---

### Post by darkod on 2009-11-19
With 9.04 you should have grub1. 9.10 comes with grub2.

But it is very strange that at least ubuntu is not booting correctly when selecting it in grub menu. Also there is entry in the menu for windows but doesn't work. It sounds like it's pointed to the wrong disk/partition.

Boot with the ubuntu cd, select option Try Ubuntu, then in terminal (Applications -> Accessories -> Terminal) execute:
sudo fdisk -l (small L)

Paste the result here. Then open menu.lst with
gedit /boot/grub/menu.lst

and look for the entries starting with title Ubuntu and title Windows. Paste the group of lines starting with title until the next empty line. So we can see where is grub looking for the OSs.

PS. The Try Ubuntu option allows you to get online, you don't have to go back to windows to paste the info, in case you didn't know.

---

### Post by EugeneS on 2009-11-19
Hi,

I will do as you suggested and provide the output of the fdisk -l and the output of menu.lst


Thanks again

---

### Post by EugeneS on 2009-11-19
Hi,

I performed the operations you suggested.
The results are following:

ubuntu@ubuntu:/dev$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x03920391

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19456   156280288+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x034a0349

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       12827   103032846   17  Hidden HPFS/NTFS
/dev/sdb2   *       13083       19457    51207187+  83  Linux
/dev/sdb3           12828       13082     2048287+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x52f688c5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121601   976760001    7  HPFS/NTFS
- Show quoted text -[/I]



Where sdb is the drive with Ubuntu installed on and also the boot loader.

When I entered gedit /boot/grub/menu.lst I found out that this file does not exist at all. In fact it seems that the /boot/grub directory does not exist.


I tried to extract MBR from both possible volumes: sdb1 and sdb2. I put a reference to boot.ini and both were failing.

P.S. I extracted the MBR using following command:
dd if=/dev/sdb(x) of=/tmp/ubuntu.mbr bs=512 count=1

---

### Post by weetoots on 2009-11-20
Weetoots here,

Well I tried to install to my 40GB drive and although 9.10 said it installed, it did worse.
I rebooted and entered right back into win 7. Checked for my drives and two were missing, the 40GB and my 250GB. I expected the 40GB because of the formating, but not my 250.
So i went back into Bios and check my drives, changed the boot sequence to start with the 40GB that supposedly had Ubuntu.
rebooted and started to enter the boot mgr and got an error 15.

So now I can't get into Ubuntu but I also somehow erased my 250GB drive in the process. YUK!
So back into the Bios reversed and rebooted back into win 7.

Used Partition Wizard and deleted both screwed up drives and reformated to NTFS. Ran an image up my C: drive so I have something to fall back on.

Now, I guess the only way I can install 9.10, which has instructions a little different that those posted, but somehow I got through it, and do a side-by-side install. Now I am nervous.

Any ideas?

Never give up. 

Al  :)

---

### Post by ezsit on 2009-11-21
Please read through the following instructions. It should walk you right through the entire install trouble free.

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

AND

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

And, eventhough it was written for Ubuntu 9.04, all basics still apply to any version of Ubuntu.

[https://help.ubuntu.com/9.04/installation-guide/i386/index.html](https://help.ubuntu.com/9.04/installation-guide/i386/index.html)

And, finally, to install within Windows and avoid partitioning if you want:

[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

Lastly, some great links to installation info:

[https://help.ubuntu.com/community/CategoryInstallation](https://help.ubuntu.com/community/CategoryInstallation)

---

### Post by weetoots on 2009-11-21
Well it still isn't working the way I want. I tried to install, again, in a side by side configuration. Ubuntu want to take a 
3rd of my 1T drive. That's not what I want.
If I make a 100GB partition on that drive and go back into install, can I make sure that Ubuntu will install there?
 I still haven't found a installation guide, that is 
specifically for 9.10. An install on a drive that has windows installed first.
I have been working on computers since 1969. Yes I am that old, but never have I been so flustered. This is very time consuming, too.

I'd like to just put the CD in and have Ubuntu install where I want it, with as little instruction from me.

Thanks for listening,
Al

---

