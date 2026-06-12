---
title: "Already have four partitions..."
date: 2011-06-06
forum: Installation &amp; Upgrades
---

### Post by adamorr on 2011-06-06
Yep, im new here. Brace for noob impact. I have searched the forum for my problem but still have some unanswered questions.

I  am trying to install Ubuntu alongside Win 7 on my HP laptop. Problem being that  it already seems to have four partitions. Which I think are... Windows  boot thing(sda1 200mb), windows(sda2 352GB), Recovery(sda3 13GB) and HP  tools(sda4 100MB). I already shrank my windows partition by 100GB before  I realised I needed more partitions so there is 100GB of unused space  too.  

I have made a set of recovery disc's already.

When I first tried to install there was no option to "install side by side with windows" so thats why I am making space and stuff for a manual installation... I think.

What  I am wondering is well.. what to do. I guess I have to delete one or  two of those partitions. But I am not sure how to go about that. If I  just delete it in the partition editor in Ubuntu I would expect that  when I boot into windows there will be problems when either my recovery  partition or my HP tools are missing. 

The other question is do I  need two free partitions to install Ubuntu? In which case I would have  to get rid of recovery and HP tools? I read something about special  partitions which can have multiple partitions inside them.. but I have  no idea what's going on there.

Thanks in advance for any advice.

---

### Post by linuxinstalledfromhdd on 2011-06-06
> **adamorr said:**
> Yep, im new here. Brace for noob impact. I have searched the forum for my problem but still have some unanswered questions.

I  am trying to install Ubuntu alongside Win 7 on my HP laptop. Problem being that  it already seems to have four partitions. Which I think are... Windows  boot thing(sda1 200mb), windows(sda2 352GB), Recovery(sda3 13GB) and HP  tools(sda4 100MB). I already shrank my windows partition by 100GB before  I realised I needed more partitions so there is 100GB of unused space  too.  

I have made a set of recovery disc's already.

When I first tried to install there was no option to "install side by side with windows" so thats why I am making space and stuff for a manual installation... I think.

What  I am wondering is well.. what to do. I guess I have to delete one or  two of those partitions. But I am not sure how to go about that. If I  just delete it in the partition editor in Ubuntu I would expect that  when I boot into windows there will be problems when either my recovery  partition or my HP tools are missing. 

The other question is do I  need two free partitions to install Ubuntu? In which case I would have  to get rid of recovery and HP tools? I read something about special  partitions which can have multiple partitions inside them.. but I have  no idea what's going on there.

Thanks in advance for any advice.

When you install Ubuntu from a live disc or live Flash Drive, you will be presented with the option to shrink one of your partitions to make room.

When I was new to Ubuntu, what I did was this.  I purchased a full set of Windows restore discs for my system from the manufacture.  When they arrived I kept them with the original packaging.  Then I completely wiped my hard drive with the Ubuntu installation USB Flash Drive.  Installation took about 10 minutes.  Then I used a walkthrough like:

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

My recommendation is to try 10.10 first. Always go with the previous release of Ubuntu just to be on the safe-side.  

Then when I was done with that I used Virtualbox 4 to install a working XP on my computer to use for everything I needed while I was slowly learning how to use the same features in Ubuntu for the same things I normally used XP for, and it even provided me with USB support for things like iTunes while I migrated my music over, and stuff like that. 

That really helped me the most. I don't even use Windows anymore at this point. I'm happy and never looking back. 

Goodluck.

---

### Post by oldfred on 2011-06-06
You only have to delete one partition as Ubuntu will work fine from the logical partitions inside an extended partition. You can also put a NTFS data/shared partition inside the extended partition and windows will use it just fine. Only use windows partitioning tools to shrink windows and use gparted to create new partitions.

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Besure to create recovery DVD(s) first.
HP tools partition discussion:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
Shrinking a Windows 7 partition is best done in Windows. 
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)
The Hedge show graphically how to delete & create partitions:
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)

Basics of partitions:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

### Post by wbloos on 2011-06-20
there is space for 4 partitions in the partition table.
if you make 4 primary partitions, there is no room in the partition table to make another partition. So it is impossible to make a 5th one then.

If that is the case , then you will need to delete 1 partition in order to make more partitions than 4.
Then you can make an extented partition, which means that the 4th record of the partition table refers to another partition table ("extended"), where you can make as many "logical" partitions as you like. They are just as real as primary partitions.

There is nothing more to it. The moment you make your 4th primary partition, the partition table is full and then you cannot make more. So the 4th partition should be an extended partition or a logical partition (depends on your software what the option is called).

HTH
If it is solved, please change to [solved]

---

### Post by srs5694 on 2011-06-20
> **wbloos said:**
> there is space for 4 partitions in the partition table.
if you make 4 primary partitions, there is no room in the partition table to make another partition. So it is impossible to make a 5th one then.

If that is the case , then you will need to delete 1 partition in order to make more partitions than 4.

Actually, it's possible to convert one or more partitions from primary to logical, although there are caveats. For more information, check out my [FixParts](http://www.rodsbooks.com/fixparts/) program and Web page.

That said, in the case of a computer with Windows pre-loaded and consuming all four primary partitions, IMHO it's usually best to create a recovery DVD set using a utility provided for this purpose in Windows, delete the ~20 GB partition that the manufacturers use instead of physical media, resize other partitions as desired, and then use the resulting free space to create a new extended partition and logical partitions within it.

Incidentally, I recently discovered that you can get "stock" Windows 7 installation DVD images from [here.](http://www.mydigitallife.info/download-windows-7-iso-official-32-bit-and-64-bit-direct-download-links/) These downloads are legal; they're available so that Windows can be sold online. You do need a valid license key, of course, for the version you download. Such keys should be printed on your computer or in a manual that came with it. IMHO, having such a disc is preferable to having a manufacturer's recovery disc set, since the latter can often be used only to restore the system to its original state, taking over the whole hard disk and installing whatever bloatware the manufacturer provided with the computer. OTOH, you may need to track down drivers for your hardware, particularly if your computer is significantly newer than Windows 7.

---

### Post by gordintoronto on 2011-06-21
Issue 41 of Full Circle Magazine deals with this exact issue, in the Q&A column.

[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)

---

