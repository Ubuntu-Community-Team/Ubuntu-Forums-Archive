---
title: "Installation of Dual boot of W7/Ubuntu14.04 halted by misalignment issue"
date: 2015-04-02
forum: Installation &amp; Upgrades
---

### Post by S.I._Chou on 2015-04-02
[FONT=arial]I am trying to install a dual boot of W7/Ubuntu14.04 using ubuntu-14.04.2-desktop-amd64.iso[/FONT]
[FONT=arial]
[/FONT][FONT=arial]While it is not uncommon to read such statements like "[COLOR=#444444][FONT=Lato]It took exactly five minutes to completely install Ubuntu and get a prompt to restart the computer,[/FONT][/COLOR][COLOR=#444444][FONT=Lato] "  my experience is unfortunately like being lost in a mind field.  [/FONT][/COLOR][/FONT]
[FONT=arial]
[/FONT][FONT=arial]My attempt to install dual boot of Ubuntu 14.04/W7 got stalled for many hours and finally saw the following complaint next morning:[INDENT][COLOR=#332E38][FONT=Palatino]**"The partition /dev/sdb5 assigned to / starts at an offset of 2048 bytes from the minimum alignment for this disk, which may lead to very poor performance.**
[/FONT][/COLOR]
[COLOR=#332E38][FONT=Palatino]**Since you are formatting this partition, you should correct this problem now by realigning the partition, as it will be difficult to change later. To do this, go back to the main partitioning menu, delete the partition, and recreate it in the same position with the same settings. This will cause the partition to start at a point best suited for this disk."**
[/FONT][/COLOR]

[/INDENT]
I hit the back keys many times and gave up as no helpful instructions were offered.  

The installing software started somewhere like DiskManagement20140920.JPG and attempted to create in my "Disk 1" a second partition which is now only shown as 304.65 GB Unallocated in "DiskManagement20150330.JPG."   

One more try on installtion got me the same complaint/warning, and now I don't see how to assign the Ubuntu partition being **/dev/sdb5.  **

**[COLOR=#545454]My F: drive is a [B]Seagate **[/COLOR][COLOR=#545454]1TB[/COLOR][COLOR=#545454] **Backup Plus** which [/COLOR][COLOR=#545454]has [/COLOR][COLOR=#545454]Sector size[/COLOR][COLOR=#545454](logical/physical): 512 bytes / 512 bytes.  [/COLOR][FONT=Verdana]Some one told me "alignment would only matter on drives with physical sector sizes > 512 bytes."    Even mis[/FONT][FONT=Verdana]alignment penalty if applicable for ext4 seems small assuming I glanced correctly 
[/FONT][http://www.ibm.com/developerworks/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/library/l-4kb-sector-disks/)
 
[/B][/FONT][FONT=arial][B]The result for "chkdsk on drive F" in W7 indicated No Problem was found. [FONT=Verdana]
[/FONT][/B][/FONT]
[FONT=arial]**Because of this complaint I wonder whether the partitioning was a healthy one and whether going ahead to get rid of the unallocated space to get a clean slate will make any difference.**
[/FONT]
[FONT=arial]**Any help to help me getting to square one will be appreciated.**[/FONT]

---

### Post by ajgreeny on 2015-04-02
**You must not make partitions for any Linux installation using the Windows Disk-management tool.**  I think your problem is a result of you doing this, if I understand your post properly as any partitions that it makes are not usable by Linux.  Unfortunately I can not tell you what the screenshots you have shown mean as I do not use Windows any more of any type or version, but I note there are 5 partitions showing which would lead me to believe that the system is perhaps using GPT partitions, and maybe UEFI, though I can not see an EFI partition which would be required if using UEFI instead of a legacy MBR BIOS.  Do you know whether you have BIOS or UEFI?

You should use the Windows disk management utility only to make unallocated space for Ubuntu which is what appears toshow in your 1TB Disk-1 from the first screenshot, but I don't remember how Windows shows ext4 partitions normally, so that 304GB may not really be unallocated at all, but just unknown to Windows.

When using the Ubuntu installation system you can either point the installer to that unallocated space and let  it and make the default partitions needed, or you could choose "Something Else" and make partitions of the sizes that you want with a separate /home or data partition if you wish.  As a first installation I suggest this will be the easiest for you.

If you really want to manage the partitions manually you must choose "Something Else" and in that 304GB space I would suggest you make an extended partition of the full 304GB if using MBR BIOS or if using GPT partitions you can ignore this as there is no partition number limit with GPT.

Now within the extended partition (for BIOS) make 3 logical partitions of approx 20GB as an ext4 partition for root, shown as / when you set the mountpoint of the new partition, 2 - 4GB as swap which needs no mountpoint and all the rest as another ext4 partition with mountpoint /home.  Put a tick in the Format box for these new partitions.  If the system does use GPT partitioning you can make the same partitions, but just forget about the extended partition as it is not necessary.

---

### Post by oldfred on 2015-04-02
The link you used is one I often post.

Not sure why you are getting an error. All recent partition tools align correctly.

The alignment must really be on 8 sector boundaries or divisible by 8.
I prefer to partition in advance as there are some slight advantages to smaller / (root) partition of 25GB and rest of drive as other partitions like /home, /mnt/data, /mnt/backup etc.

       Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)

After partitioning post this:

 sudo parted /dev/sdb unit s print

You cannot use Windows NTFS for Linux, ex4 is the standard format.
      
 Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using)

   Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

---

### Post by S.I._Chou on 2015-04-02
[FONT=arial]Hi, ajgreeny and oldfred,[/FONT]

[FONT=arial]I am very lucky to have you two knowledgeable people responding to my inquiry so promptly.  (oldfred:  the two paragraphs' quote and the last link in my inquiry were in fact from this page you posted [install/partition issue - goto: answer]("http://gotoanswer.stanford.edu/installpartition_issue-4866315/") )[/FONT]

[FONT=arial]I don't think I have explictly made Linux partitions using Windows' tool since I made this DVD from  Ubuntu14.04 iso.  The W7's disk management screen shots are used to help communicate.  Since I did not go through Unix route, some of you folks comments are beyond my pay grade.  So please tolerate possible inaccuracy of my statements.  As my OS is W7, I have only BIOS and no UEFI.  [/FONT]
[FONT=arial]
[/FONT][FONT=arial]About a year ago, I tried 12.04 and did manage to have dual boot installed.  But shortly afterward a wishful touch up on the booting script got my PC "blow up," i.e., I could not boot to either of the dual.  I had to use Terabyte's  BootIt Bare Metal (BIBM) to bale me out, even though only for single boot to W7.  It entailed disk image restoration etc.  I washed hand on 12.04.  Details are fuzzy now.  The first W7's disk management screen shot seemed to indicate no trace of Linux partition.  [/FONT]
[FONT=arial]
[/FONT][FONT=arial]In between my two failed 14.04 installation attempts I de-installed BIBM to avoid possible conflict with later dual boot installation which has not occurred yet.[/FONT]
[FONT=arial]
[/FONT][FONT=arial]oldfred gave me lots to read to fill in my lack of basics.  On the other hand as my Disk-1 has only W7 backup files there and there are copies stored off PC too.  I don't mind to have the disk reformatted if this will make a cleaner slate to simplify the work.[/FONT]

---

### Post by oldfred on 2015-04-02
Some suggest physically disconnecting the Windows drive, so when you install Ubuntu it can only be on its drive. But then be sure to reconnect Windows drive so it is first drive or sda in Linux. 

If not disconnecting drive, then with the Something Else install option you must choose where to install the grub2 boot loader. It will default to sda, which usually is the Windows drive. Better not to overwrite Windows boot loader in sda, and install grub's boot loader to sdb and set BIOS to boot from sdb.

---

### Post by S.I._Chou on 2015-04-10
I have implemented most of the advices from ajgreeny and oldfred, it seems the installation was OK but there is only [COLOR=#000000][FONT=Ubuntubeta]automatic direct booting to W7.  [/FONT][/COLOR]
[INDENT][COLOR=#000000][FONT=Ubuntubeta]The alignment must really be on 8 sector boundaries or divisible by 8.[/FONT][/COLOR]
[/INDENT]
[INDENT][INDENT][FONT=Ubuntubeta][COLOR=#000000]The "Align to" choices in GParted have only Cylinder, MiB, and None, so I chose [/COLOR][/FONT][COLOR=#000000][FONT=Ubuntubeta]MiB.  And by try and error it seems I need to also use "Free space preceding (MiB) =1"[/FONT][/COLOR]

[/INDENT]
[/INDENT]
[INDENT][COLOR=#000000][FONT=Ubuntubeta]rest of drive as other partitions like **/home, /mnt/data, /mnt/backup** etc.[/FONT][/COLOR]
[/INDENT]
[INDENT][INDENT][COLOR=#000000][FONT=Ubuntubeta]More instruction for  [/FONT][/COLOR]**/mnt/data, /mnt/backup ??**

[/INDENT]
[/INDENT]
[INDENT]
**[COLOR=#000000][FONT=Ubuntubeta]If  you really want to manage the partitions manually you must choose  "Something Else" and in that 304GB space I would suggest you make an [B]extended partition of the full 304GB** if using MBR BIOS.[/FONT][/COLOR]

[COLOR=#000000][FONT=Ubuntubeta]Now within the extended partition (for BIOS) make **3 logical partitions** of [/FONT][/COLOR][/B]
[/INDENT]
[INDENT][INDENT]**[COLOR=#000000][FONT=Ubuntubeta]approx 20GB as an ext4 partition for [B]root**, shown as / when you set the mountpoint of the new partition, [/FONT][/COLOR][/B]
**[COLOR=#000000][FONT=Ubuntubeta]2 - 4GB as [B]swap** which needs no mountpoint   (I have 12 GB RAM , what about  **hibernation** ??)[/FONT][/COLOR][/B]
**[COLOR=#000000][FONT=Ubuntubeta]and all the rest as another ext4 partition with mountpoint [B]/home**. Put a tick in the Format box for **these** new partitions. [/FONT][/COLOR][/B]
[/INDENT]
[/INDENT]
[INDENT][B][COLOR=#000000][FONT=Ubuntubeta]
[/FONT][/COLOR][/B]
[B][COLOR=#000000][FONT=Ubuntubeta]After partitioning post this:[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntubeta]sudo parted /dev/sdb unit s print[/FONT][/COLOR][/B]

[B][COLOR=#000000][FONT=Ubuntubeta]
[/FONT][/COLOR][/B]
**[COLOR=#000000][FONT=Ubuntubeta]Any install with [B]Something Else** which is required with **external drives or any second drive** or any install with separate /home[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntubeta]
[/FONT][/COLOR][/B]
[B][COLOR=#000000][FONT=Ubuntubeta]?? Also shows combo box with location of grub2 boot loader[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntubeta]
[/FONT][/COLOR][/B]
[/INDENT]
[INDENT][B][COLOR=#000000][FONT=Ubuntubeta]With  the Something Else install option you must choose where to install the  grub2 boot loader. It will default to sda, which usually is the Windows  drive. Better not to overwrite Windows boot loader in sda, and [B]install grub's boot loader to sdb and 

[/B][/FONT][/COLOR]**??  and set BIOS to boot from sdb**[/B][/INDENT]
[INDENT][INDENT]**[B][COLOR=#000000][FONT=Ubuntubeta]I  do not understand this and the "combo box" mentioned above and these  were not implemented.  They are probably responsible for the only  automatic direct booting to W7.  Hope the rest of [/FONT][/COLOR]the installation is OK.  Probably need to use Live CD to get back to Ubuntu.**[/B]
[/INDENT]
[/INDENT]

---

### Post by yancek on 2015-04-10
When using the "Something Else" manual installation option, you will see a window which lists the partition(s) and drives attached in the main windows.  Immediately below that window you will see "Device for bootloader installation" and the default as mentioned above, would be "/dev/sda".  That would be the master boot record of the first drive.  The option you should have used would be "/dev/sdb" if it was shown.  I don't know if you dis-connected the windows drive before installing.  After the install, did you change the BIOS to boot from the second drive, the one on which you installed Ubuntu.  You should see a message on boot telling you which key to press to "Enter Setup", then look for a Boot tab in the new windows.

---

### Post by oldfred on 2015-04-10
This shows red box around the combo box.
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

If booting Windows they unlikely that you installed grub to sda or the Windows drive. If you disconnected Windows drive then default of sda is ok as that was only drive, but it becomes sdb when you plug it back in.

In BIOS which should be a quick screen you see just as system starts, you need to change boot order to drive that is sdb first and sda second. See computer or motherboard manual for key to get into BIOS often del or f2 keys but only just as system starts.

Update on swap.
Ubuntu boots quick enough that hibernation does not save much and often adds issues.
Also you only need swap equal to RAM in GiB (not GB) to full hibernate all of RAM. Old rule of 2X RAM was back when systems only had KB of RAM and then you needed 1 or 2GB of swap. And now 2GB of swap just to have some is all you will need unless editing videos or doing some extreme tasks. With normal use, and 4GB of RAM I never use swap.

---

### Post by S.I._Chou on 2015-04-12
Thanks, oldfred.  Your clarification is crucial for me to understand the  fine prints of these web instructions.  I have changed boot order to  drive that is sdb first and sda second.  

Wish there is a way to  use a single click to choose which one to boot.  Right now if the  default boot choice is not what I want I need to change and save the  BIOS.

---

### Post by oldfred on 2015-04-12
Grub menu should let you choose. If not:
sudo update-grub

And you should have a one time boot key. Often f10 or f12 but varies by brand of computer, see manual. And it may just show hard drive, but then have sub-menu for which drive.

---

