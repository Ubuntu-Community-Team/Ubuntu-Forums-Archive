---
title: "Partitiion limit problem on Win7 laptop when installing Ubuntu AMD64"
date: 2010-11-26
forum: Installation &amp; Upgrades
---

### Post by hpng on 2010-11-26
[FONT=Century gothic, sans-serif][SIZE=2]I want to install Ubuntu 64 on my HP laptop.[/SIZE][/FONT]
 [FONT=Century gothic, sans-serif][SIZE=2]It already has 4 primary (OEM) partitions:[/SIZE][/FONT]
 

 [FONT=Century gothic, sans-serif][SIZE=2]Here it is:[/SIZE][/FONT]
 

 [FONT=Century gothic, sans-serif][SIZE=2]Partitions on one and only HP laptop disk drive (DISK O): [/SIZE][/FONT] 
 [FONT=Century gothic, sans-serif][SIZE=2]Volume Layout Type File System Status Capacity Free Space % Free[/SIZE][/FONT]
 [FONT=Century gothic, sans-serif][SIZE=2](C:) Simple Basic NTFS Primary Partition 445.34 GB 403.53 GB 91[/SIZE][/FONT]
 [FONT=Century gothic, sans-serif][SIZE=2]HP_TOOLS Simple Basic FAT32 Primary Partition 99 MB 92 GB 93[/SIZE][/FONT]
 [FONT=Century gothic, sans-serif][SIZE=2]Recovery (D:) Simple Basic NTFS Primary Partition 20.12 GB 2.93 GB 15[/SIZE][/FONT]
 [FONT=Century gothic, sans-serif][SIZE=2]System Simple Basic NTFS Primary Partition 199 MB 165 MB 83[/SIZE][/FONT]
 

 

 [FONT=Century gothic, sans-serif][SIZE=2]As I understand it, I can only have a max of 4 primary partitions per disk drive.[/SIZE][/FONT]
 [FONT=Century gothic, sans-serif][SIZE=2]I do not want to delete any OEM partition because they are critical to laptop recovery.[/SIZE][/FONT]
 

 [FONT=Century gothic, sans-serif][SIZE=2]During Ubuntu 64 install, it gave me two choices:[/SIZE][/FONT]
 
[LIST=1]
[*][FONT=Century gothic, sans-serif][SIZE=2]Erase 	the entire disk, and 2) manual partioning.:[/SIZE][/FONT]
[/LIST]
 

 [FONT=Century gothic, sans-serif][SIZE=2]Since I already have a max of 4 primary partitions, so I cannot create any new partition.[/SIZE][/FONT]
 [FONT=Century gothic, sans-serif][SIZE=2]This is the point where I have to abandon my install... because as I understand it, Kinux needs to reside in primary partition, and I do not have a new one for it.[/SIZE][/FONT]
 [FONT=Century gothic, sans-serif][SIZE=2]Except for the C: partition, the other OEM ( factory) partitions are quite small.[/SIZE][/FONT]
 [FONT=Century gothic, sans-serif][SIZE=2]Ouch![/SIZE][/FONT]
 

 [FONT=Century gothic, sans-serif][SIZE=2]NOTE: Someone mentioned I use Wubi to install. But I peek at the contents of Ubuntu AMD64 iso file and it already has Wubi.exe in it. So I assume Wubi ran when I start Ubuntu64 install.[/SIZE][/FONT]
 

 

 [FONT=Century gothic, sans-serif][SIZE=2]Please advice.[/SIZE][/FONT]
 [FONT=Century gothic, sans-serif][SIZE=2]I am a Linux newbie.[/SIZE][/FONT]
 

How do I get this forum to send me email when someone respond to my posting?


 [SIZE=2][FONT=Century gothic, sans-serif]
[/FONT][/SIZE] [FONT=Century gothic, sans-serif][SIZE=2]Thanks,[/SIZE][/FONT]
 [FONT=Century gothic, sans-serif][SIZE=2]HP[/SIZE][/FONT]

---

### Post by conradin on 2010-11-26
Heres a good explanation of why you cant have more than 4 primary partitions. What you will need is to use logical partitions.
[http://www.linuxquestions.org/questions/linux-general-1/creating-more-than-4-primary-partitions-376698/](http://www.linuxquestions.org/questions/linux-general-1/creating-more-than-4-primary-partitions-376698/)

---

### Post by sikander3786 on 2010-11-26
Ubuntu doesn't need a primary partition. It can boot from an Extended/Logical partition as well. So what you need to do is choose manual partitioning and then create an Extended partition and inside that, I would recommend to create 3 Logical partitions. Remember, Extended Partition itself is a primary partition so you definitely need to delete one of your Primary Partitions to do that ;-)

1. Ubuntu partition, Mount point /, FS ext4 size > 8 GB

2. /home partition, Mount Point /home, FS ext4, size = custom as this is the partition you will be storing your personal files and settings to. The more the size, the comfortable you are.

3. Swap partition, size = RAM x 2.

Remember, /home is not absoulutely necessary and you can do well with only 2 partitions. /home is recommended in the sense that in case of a re-install, you don't lose your personal files and settings.

Wubi is intended for testing purposes only and it is a bit slower, bit problematic and has issues with some updates. So a proper dual-boot is the way to go.

Prior to installing Ubuntu, boot into a Live CD, test all your hardware with that and from Applications > Accessories > Terminal, post the output of this command.

```
sudo fdisk -lu
```

It would tell us more about your current partition setup.

---

### Post by hpng on 2010-11-26
[FONT=Century gothic, sans-serif][SIZE=1]:[/SIZE][/FONT]Thanks.

 [FONT=Century gothic, sans-serif][SIZE=1]Here is my current hard drive setup:[/SIZE][/FONT]
  

  [FONT=Century gothic, sans-serif][SIZE=1]Partitions on one and only HP laptop disk drive (DISK O): [/SIZE][/FONT] 
  [FONT=Century gothic, sans-serif][SIZE=1]Volume Layout Type File System Status Capacity Free Space % Free[/SIZE][/FONT]
  [FONT=Century gothic, sans-serif][SIZE=1]-(C   :) Simple Basic NTFS Primary Partition 445.34 GB 403.53 GB 91[/SIZE][/FONT]
  [FONT=Century gothic, sans-serif][SIZE=1]-HP_TOOLS Simple Basic FAT32 Primary Partition 99 MB 92 GB 93[/SIZE][/FONT]
  [FONT=Century gothic, sans-serif][SIZE=1]-Recovery (D   :) Simple Basic NTFS Primary Partition 20.12 GB 2.93 GB 15[/SIZE][/FONT]
  [FONT=Century gothic, sans-serif][SIZE=1]-System Simple Basic NTFS Primary Partition 199 MB 165 MB 83[/SIZE][/FONT]


     [FONT=Century gothic, sans-serif][SIZE=1]As I mentioned before and shown above, I already have 4 primary partitions on the disk.[/SIZE][/FONT]
  [FONT=Century gothic, sans-serif][SIZE=1]So, how do I create an extended partition  on this drive in addition to leaving the above 4 primary partition alone?[/SIZE][/FONT]
[FONT=Century gothic, sans-serif][SIZE=1]I am ok with shrinking the C: drive above since it has a lot of space.[/SIZE][/FONT]
[FONT=Century gothic, sans-serif][SIZE=1]
[/SIZE][/FONT]

---

### Post by wilee-nilee on 2010-11-26
If you can't remove one of the partitions install with wubi just burn a cd of it and open it from computer in admin and install. A extended will only work with 3 basic primary types.

also when you post those partition descriptions put them in code tags look in my signature as to how to other wise it makes it easy to misread them. We need to see things lined up in order correctly.

You can't add a extended to what you have.

---

### Post by hpng on 2010-11-26
I still have a problem with loosing linux data if I have to reinstall Win 7 since
Linux will now reside in C: drive if I use Wubi.
Here is an alternative idea with reference to my disk information below:
 ```


Partitions on one and only HP laptop disk drive (DISK O):

Volume Layout Type File System Status Capacity Free Space % Free
-(C:) Simple Basic NTFS Primary Partition 445.34 GB 403.53 GB 91
-HP_TOOLS Simple Basic FAT32 Primary Partition 99 MB 92 GB 93
-Recovery (D:) Simple Basic NTFS Primary Partition 20.12 GB 2.93 GB 15
-System Simple Basic NTFS Primary Partition 199 MB 165 MB 83
 
```

Windows defragment tool lets user resize (shrink or extend) a partition.
C drive and D (RECOVERY) drive are adjacent to each other as shown on defragment tool.
I can shrink C drive by 100 GB ro 200 GB, and then extend  D partition by as much.
Then I can put all Linux install and all linux data  on D drive.
Would that work?
if so, can i also access data on C: drive partition when linux is running on d drive?
Do I also loose linux data when I upgrade or reinstall linux on D: drive?
 Is there a reason to not use D:  drive?

---

### Post by dino99 on 2010-11-26
make room by shrinking partition(s), then you can create an extented partition. Ubuntu can be installed where you want, no matter.

here is how to install:


use gparted or partedmagic to create 3 partitions:
- / : root, bootable, ext4, ~ 12 Gb (take note of its name: /dev/sd? , will be asked when installing in manual mode by the "alternate" iso.
- swap : about 2 Gb (4 Gb if suspend/hibernate will be used)
- /home : ext3 or ext4 format, unlimited space to store your data and settings

[http://partedmagic.com/](http://partedmagic.com/)

---

### Post by hpng on 2010-11-26
I cannot create a new partition.
```

 [FONT=Century gothic, sans-serif][SIZE=2]Partitions on one and only HP laptop disk drive (DISK O): [/SIZE][/FONT] 
 [FONT=Century gothic, sans-serif][SIZE=2]Volume Layout Type File System Status Capacity Free Space % Free[/SIZE][/FONT]
 [FONT=Century gothic, sans-serif][SIZE=2](C:) Simple Basic NTFS Primary Partition 445.34 GB 403.53 GB 91[/SIZE][/FONT]
 [FONT=Century gothic, sans-serif][SIZE=2]HP_TOOLS Simple Basic FAT32 Primary Partition 99 MB 92 GB 93[/SIZE][/FONT]
 [FONT=Century gothic, sans-serif][SIZE=2]Recovery (D:) Simple Basic NTFS Primary Partition 20.12 GB 2.93 GB 15[/SIZE][/FONT]
 [FONT=Century gothic, sans-serif][SIZE=2]System Simple Basic NTFS Primary Partition 199 MB 165 MB 83[/SIZE][/FONT]

```
 

 [FONT=Century gothic, sans-serif][SIZE=2]As I understand it, I can only have a max of 4 primary partitions per disk drive.[/SIZE][/FONT]
 [FONT=Century gothic, sans-serif][SIZE=2]I do not want to delete any OEM partition because they are critical to laptop recovery.[/SIZE][/FONT]
 
that is why I rather shrink C partition, and extend D partition.
See my previous post.

thanks.

---

### Post by sikander3786 on 2010-11-26
> Then I can put all Linux install and all linux data on D drive.

Installing Ubuntu to the D: drive would over-write any data previously present on it. If you can empty that some how, (you'll need to burn that recovery stuff to DVDs then) I'd recommend to create an Extended partition with 2 Logicals as the Ubuntu Root and Swap partitions.

You can access data from NTFS drives just fine in Linux.

And if you've a proper dual-boot install, updates shouldn't break it. And even if they do (very rare), it is fixable most of the time.

And there is no apparent reason not to use D: drive.

---

### Post by wilee-nilee on 2010-11-26
[ATTACH]176613[/ATTACH]

So here is my W7 set up one partition, I have the full image backed up and the install dvd, this is really if you want Ubuntu; the set up. You could have a extra NTFS for shared data if needed. The way your going about this is rather haphazard, and installing Wubi to other then the OS partition is asking for even more trouble then it is already, at least the local expert on wubi says this.;)

The full image back up slides back in still activated.

---

### Post by sikander3786 on 2010-11-26
Ok. I just wanted to clear up things a bit as I have been posting some crap in this thread :-)

1. You cannot add another partition whether primary or extended to your current setup.

2. If you want to add it, one way of doing that is to make DVD backups of your recovery partition and then delete that partition and create an extended in its place. Then you'd obviously need to rely on the DVDs for restoring your system anytime later.

3. Another workaround will be download a Windows 7 repair disc (easily available online), delete your System Reserved partition and then move your Windows 7 boot files to the C: drive instead. Thus you'll get rid of a primary partition and would be able to create a new extended partition. A bit dangerous to do if you don't feel confident. The system would become un-bootable until the boot gets fixed.

4. Most important of all that, if you are unsure of anything, if you don't feel confident about all that stuff. **Don't do it.**

The easiest workaround for you would be to install Ubuntu using Wubi as previously mentioned in the above posts. Or even to install it as a Virtual machine inside Windows (this would be a bit more slow and the 3d stuff would be choppy).

Hope this clears some of your doubts now.

---

### Post by wilee-nilee on 2010-11-26
> **sikander3786 said:**
> Ok. I just wanted to clear up things a bit as I have been posting some crap in this thread :-)


Hey welcome to the club its always nice to have a new member. The other person dino99 wont admit this and they are a experienced user.;)

---

### Post by wayne128 on 2010-11-26
Read your posts on HP laptop.
This is not the first time I read about this. Several people encountered this issue.
I learned from another forumer elsewhere, did it myself and helped some to overcome this 'limit of 4'. Here is what the simplified ideas and procedure I though you might be interested.

1. Copy out your HP_Tool, this is just some software. 
One you copy these out to external USB stick, keep it, will bring back after partitioning. 
Or just save it in window directory. You could check to see yourself what are these tools under windows OS.

2. Shrink your biggest partition, as there is no  fdisk -l information I do not know which partition number, however it is  not too important, as long as you get the correct method.

3. Now, delete the HP_Tool small partition, this is the way to "Free the hard disk from that limit of 4 Primary".
Because once you got rid of this partition, it has left 3 primary, and  you can create the fourth which will become extended partition for your  drive.

Do not worry too much, if you worried about this step then you just stop proceeding.
It is your call. 
But many people  get through this step and enjoy the 'freedom'.

4. Because of partition shrinking on step 2, you would see a big unallocated  space, which is sandwitched between two primary partitions, this alone  give you some trouble on partition manager. This is easier to see on gparted since it is Graphic interface.
What you do now is use gparted and 'shift' the higher number partition  toward the small number partition so that the 'unallocated space' will  move to the right hand side. 
Make them adjacent to each other. leave no gap, or just a  very small ( 1MegaByte).
Select 'cylinder' on gparted GUI so that you do not have overlapping cylinder.

5. Do the same for another partition (number 3) which hold your 'recovery' 

at the end you would see that all the three primary partitions are now  adjacent to each other, leaving one large unallocated partition on you  'right side'  as viewed from gparted GUI.

6. Now, create or add the rest of unallocated space to be EXTENDED  partition. Once this is done it will become /dev/sda4, just a container  for all logical partitions to be added next few steps. you will not be  using /dev/sda4.

7. Now add whatever you want for Linux partitions. such as Swap, /, etc. 
it will automatically be assigned with /dev/sda5 then 6,7, and so on when you add more.

8. If you wish you could add a FAT32 partition and use it to copy those HP_Tool.
Alternatively create a directory in windows and copy there.

9. Next step is just install your preferred Linux OSes on these logical partitions.

OK below is my existing fdisk -l for one of the multi boot computers, you  can see first three partitions are window 7 partitions but mine are  boot, OS , data
After that extended and lots of Linux OS, at the end there are still 100G free space , I  add new partition when I play with new release...test alpha or beta release, etc.

good luck on your adventure... and be :D when 'freedom' is achieved.

> 
[root@localhost ~]# fdisk -l

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x98000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          12       96358+   6  FAT16
/dev/sda2              13        1110     8818795    7  HPFS/NTFS
/dev/sda3            1111       36806   286720000    7  HPFS/NTFS
/dev/sda4           36806       63526   214629460    5  Extended
/dev/sda5           36806       37201     3173896+  82  Linux swap / Solaris
/dev/sda6           37202       39126    15461035   83  Linux
/dev/sda7           39127       41051    15462531   83  Linux
/dev/sda8           41052       43014    15767766   83  Linux
/dev/sda9           43015       44978    15775798+  83  Linux
/dev/sda10          44979       46954    15872188+  83  Linux
/dev/sda11          46955       49504    20482843+  83  Linux
/dev/sda12  *       49505       53377    31109841   83  Linux
/dev/sda13          53378       55968    20812112   83  Linux
/dev/sda14          55969       58518    20482843+  83  Linux
/dev/sda15          58519       59793    10241406   83  Linux
/dev/sda16          59794       61009     9764864   83  Linux
/dev/sda17          61010       62310    10450251   83  Linux
/dev/sda18          62311       63526     9767488+  83  Linux
[root@localhost ~]# 

---

### Post by hpng on 2010-11-26
[SIZE=2]
[/SIZE]
[SIZE=2]Wayne:[/SIZE]
[SIZE=2]
[/SIZE]
[SIZE=2]1. Copy out your HP_Tool, this is just some software.[/SIZE]
 [SIZE=2]One you copy these out to external USB stick, keep it, will bring back after partitioning.[/SIZE]
 [SIZE=2]Or just save it in window directory. You could check to see yourself what are these tools under windows OS.[/SIZE]
 

 [SIZE=2]Jut want tomake suer, I am using Win 7 64 bit.[/SIZE]
 [COLOR=#0000ff][SIZE=2]I could not see HP_tools directory from [/SIZE][/COLOR] 
 [COLOR=#ff0000][FONT=Century gothic, sans-serif][SIZE=1]Partitions on one and only HP laptop disk drive (DISK O): [/SIZE][/FONT][/COLOR] 
 [COLOR=#ff0000][FONT=Century gothic, sans-serif][SIZE=1]Volume Layout Type File System Status Capacity Free Space % Free[/SIZE][/FONT][/COLOR]
 [COLOR=#ff0000][FONT=Century gothic, sans-serif][SIZE=1]-(C:) Simple Basic NTFS Primary Partition 445.34 GB 403.53 GB 91[/SIZE][/FONT][/COLOR]
 [COLOR=#ff0000][FONT=Century gothic, sans-serif][SIZE=1]-HP_TOOLS Simple Basic FAT32 Primary Partition 99 MB 92 GB 93[/SIZE][/FONT][/COLOR]
 [COLOR=#ff0000][FONT=Century gothic, sans-serif][SIZE=1]-Recovery (D:) Simple Basic NTFS Primary Partition 20.12 GB 2.93 GB 15[/SIZE][/FONT][/COLOR]
 [COLOR=#ff0000][FONT=Century gothic, sans-serif][SIZE=1]-System Simple Basic NTFS Primary Partition 199 MB 165 MB 83[/SIZE][/FONT][/COLOR]
 

 [COLOR=#0000ff][SIZE=2]Here is the relative physical location of all the primary partitions [/SIZE][/COLOR] 
 [COLOR=#0000ff][SIZE=2]System     |  C:          |  RECOVERY D: | HP_TOOLS[/SIZE][/COLOR]
 [COLOR=#0000ff][SIZE=2]199 MB   |   445 GB |    20 GB              |  99 MB[/SIZE][/COLOR]
 

 [COLOR=#0000ff][SIZE=2]The above information viewed from Disk Management application.[/SIZE][/COLOR]
 [COLOR=#0000ff][SIZE=2]I CANNOT see HP_Tools and SYSTEMS directory / partition from “COMPUTER” For some reason, HP did not put a partition letter like C D or E after the name of the partition for SYSTEM and HP_TOOLS.[/SIZE][/COLOR]
[COLOR=#0000ff][SIZE=2].[/SIZE][/COLOR]
 [COLOR=#0000ff][SIZE=2]It only display C: and Recovery D: partition.[/SIZE][/COLOR]
 [COLOR=#0000ff][SIZE=2]However, I can see all the above partitions when I use computer management application[/SIZE][/COLOR]
 [COLOR=#0000ff][SIZE=2]Issue:  So how do I copy contents of HP_Tools partition to a CD if I cannot see it from Windows 7 with COMPUTER application ( similar to Windows explorer)
[/SIZE][/COLOR]
 [COLOR=#0000ff][SIZE=2]Is there an application that would let me see all files in all partitions / directories on Win 7?[/SIZE][/COLOR]
 

Did you have the same partitions and setup as I do on my laptop?





 [SIZE=2]Please advice.[/SIZE]

---

### Post by wayne128 on 2010-11-26
oh, they made it hidden. 
try clonezilla , partedmagic live cd, or even use command dd to copy the 'hidden partition'
google each term and read..
the key is you can always clone out anything, the whole drive, a hidden partition, etc

if you want to unhide, google something like "how to unhide window 7 file" "how to unhide window 7 folder" or similar phrase. here is one example
[http://windows7themes.net/how-to-unhide-hidden-files-in-windows-7.html](http://windows7themes.net/how-to-unhide-hidden-files-in-windows-7.html)

no i do not have HP, mine is Dell, similar issue but I redo all partitions to look like earlier post and multi boot.

if you are interest to see another forumer who has HP laptop, go read this thread, . you can always join in and ask in detail how he did it 
[http://www.pclinuxos.com/forum/index.php/topic,82833.0.html](http://www.pclinuxos.com/forum/index.php/topic,82833.0.html)

---

### Post by bcbc on 2010-11-26
What I discovered on my Dell is this:
If you change the drive partitions as they shipped it, the recovery mechanism doesn't work.
If you remove the Dell specific bootloader, the recovery mechanism doesn't work.

I don't know what HP requires... but, if you intend to use the recovery feature, you should check what their restrictions are (and I'd backup the disk MBR as well)

In my case, I just reinstalled from DVD and downloaded the drivers I needed.

PS a lot of wubi users have accidentally installed grub to the MBR, so even using wubi is no guarantee that your HP bootloader is secure.

---

