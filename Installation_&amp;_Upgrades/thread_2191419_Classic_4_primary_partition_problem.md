---
title: "Classic 4 primary partition problem"
date: 2013-12-02
forum: Installation &amp; Upgrades
---

### Post by SuperFreak on 2013-12-02
I have a HP Pavillion DV7 laptop with 4 primary partitions(all windows). I know there various ways of doing this like deleting the HP Tools partition and resizing C but I wonder if this alternative will work for installing Ubuntu as a dual boot. I notice that the Windows program Easus Partition manager has the option of changing Primary partitions to Logical (or vice versa)on the fly. Is there any good reason why after the appropriate backup I couldn't change the C drive which is quite large to logical and then shrink it and using the left over unallocated space create an Ubuntu install? I am assuming that changing a drive to logical this way does not delete the data on the partition or prevnt it from booting.
I believe the 4 partitions on my HD are HP Tools, Recovery, System and a quite large C Drive with all the programs and Windows on it

---

### Post by Mark Phelps on 2013-12-02
Since you're planning on messing around with the Win7 "C" partition, you should really post your concerns to the Windows 7 forum: sevenforums.com.

If you change the "C": partition, my guess is that Win7 will no longer boot -- but I've generally followed the maxim "if it ain't broke, don't fix it" -- meaning, Windows has enough problems working OK as is, messing around with it's primary OS partition is asking for trouble.

---

### Post by SuperFreak on 2013-12-02
OK I tried to change c drive to logical but Easus won't let me because it is a system partition. So I converted HP Tools to logical . I then resized the C drive producing 120GB of unallocated space for Ubuntu. Easus say that there are 3 primary partitions (including c) and 2 logical (HP Tools and unallocated). So I booted to Gparted and tried to work with the unallocated space but it will not let me create a partition there it says I have too many primary partitions. Any suggestions short of deleting Windows partitions?

Oh I did try to attach screen shots from Easus but the forum is not accepting the shots (tried bmp,jpg and jpeg all small files from screen shots)

---

### Post by SuperFreak on 2013-12-02
> **Mark Phelps said:**
> Since you're planning on messing around with the Win7 "C" partition, you should really post your concerns to the Windows 7 forum: sevenforums.com.

If you change the "C": partition, my guess is that Win7 will no longer boot -- but I've generally followed the maxim "if it ain't broke, don't fix it" -- meaning, Windows has enough problems working OK as is, messing around with it's primary OS partition is asking for trouble.


Thanks I must have posted at the same time as you. Yes I found out I can't changes the OS partition to logical. 
It seems to me that I am asking how to install Ubuntu on a Win 7 machine without compromising Windows so the Ubuntu forums seemd a logical place to ask. I had gone to an HP forum with the same question and that is where I saw the option to convert C drive to logical
[http://h30434.www3.hp.com/t5/Other-Notebook-PC-Questions/How-to-repartition-HDD-of-HP-notebook-with-pre-installed/td-p/742019]("http://h30434.www3.hp.com/t5/Other-Notebook-PC-Questions/How-to-repartition-HDD-of-HP-notebook-with-pre-installed/td-p/742019")

---

### Post by ubfan1 on 2013-12-02
I have no idea what EASUS does, but if it is using dynamic paritions, that won't work for you.  Generally, you backup the small partition at the end (tools?), delete the partition, defrag the C partition (which should be the last one now), and then shrink it from the right, leaving a big block of free space.  In the free space, make an extended partition (which is the 4 th primary now), an within the extended, make a logical for the tools (and restore it from your backup), and make logical partitions for Ubuntu root and swap (and whatever else you want like home).  BACKUP everything on the system however! When changing partitions, things can go horribly wrong.
Good Luck.

---

### Post by SuperFreak on 2013-12-02
Thanks Ubfan
I wanted to avoid deleting Windows partitions entirely but it seems HP has made this virtually impossible. I realize if I delete HP Tools as you say I will have fewer primary partitions allowing me to create an Extended partition with logical partitions. But does that not mean that I will not be able to install HP Tools again because I will not be able to create a primary partition again without wiping Ubuntu. It is a mystery why OEM manufacturers have created this conundrum( guess it is about $)

edit:It appears from my screenshot that there are now only 3 primary partitions why can I not format the unallocated space?

---

### Post by oldfred on 2013-12-02
It looks like you have a d: between the unallocated and HP tools. You can only have one extended partition and all logical partitions must be in the extended. No primary partition can be in between the logicals.

       My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor utility partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. - gordintoronto
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)
This suggests removing system partition and making c: the bootable partition. But has details on all alternatives
[http://h30434.www3.hp.com/t5/Other-Notebook-PC-Questions/How-to-repartition-HDD-of-HP-notebook-with-pre-installed/td-p/742019](http://h30434.www3.hp.com/t5/Other-Notebook-PC-Questions/How-to-repartition-HDD-of-HP-notebook-with-pre-installed/td-p/742019)
Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)

---

### Post by SuperFreak on 2013-12-02
Thanks Old Fred
Would it be possible to move one of those partitions so Unallocated and Logical are adjacent
I know using Gparted to move partitions around is quite time consuming would it be better to make clones of HP Tools and the primary partition and then switch their relative positions?


Edit: Ok Old Fred I had a look at your links some of which I have already read. The reason I started this post was to see if there was a way of installing Ubuntu on a computer with 4 primary partitions without losing them permanently. The idea of backing up HP Tools and then deleting that partition comes closest to what I want. The problem is that although you have backed up HP Tools there is no way of reinstalling it once you have Ubuntu on the system because then you have the 4 primary partition dilemma again. My solution is to make HP Tools a logical drive. I was able to boot to that drive and see the tools once I did this so I don't think it matters if it is logical or primary. The next matter which I did not understand is to make the unallocated space from C adjacent to the logical HP Tools partitioning.I am hoping all I need do is shrink drive D at it's beginning by 100 MB and then copy HP Tools into that partition and then expand D into the old HP Tools partition space.
Does that sound reasonable?

---

### Post by fantab on 2013-12-02
HP Tools partition contains HP Tools.. You can copy these tools either on a separate partition or on a separate drive/disk externally. Also its a very small partition with only 100Mb of space.

Your best option is to delete HP Tools partition and convert the space gained by shrinking \C:, Unallocated space to EXTENDED partition and have Logical partitions on it. If you want you can create a Logical partition of about 100Mb and copy back HP Tools in it.
The 100Mb space you have as 'unallocated' at the end after deleting HP tools partition can be merged with \D.

If I were you, I would SHRINK my C  more, I'd reduce it to like 150GB. 
[Windows will NOT allow 'Shrinking' beyond a point, that's because of enabled Hibernation function. Follow the discussion here for more info: [http://www.sevenforums.com/tutorials/2672-partition-volume-shrink-17.html](http://www.sevenforums.com/tutorials/2672-partition-volume-shrink-17.html)]

---

### Post by SuperFreak on 2013-12-02
I will give it a try tomorrow if I have time,,,Thanks

---

### Post by Mark Phelps on 2013-12-02
Since you have decided to mess around with "C:" anyway, BEFORE you do that, at least do yourself the favor of using the Win7 Backup feature to create and burn a Win7 Repair CD.  You will need this to restore Win7 boot capability -- should something go wrong during your dual-boot setup.

Also, I can't overemphasize the importance of using ONLY Windows partitioning tools to shrink the "C:" partition for Win7.  It's generally best to use the Win7 Disk Management tool to do this, but if the EASEUS tool is also a Windows product, it should work OK, as well.

---

### Post by SuperFreak on 2013-12-03
Thanks Mark

I successfully installed Ubuntu on my laptop and Windows is intact, including the HP Tools partition. Most of the instructions I found on the web indicated this partition had to be deleted in order to install Ubuntu in a Dual boot with Win 7. I didn't want to do that because HP Tools contains some useful tools but ,more importantly it contains a back up of the BIOS. Just in case anyone else wonders how I did this here is a brief run down:

1a) Back up all your important files
1b) Defrag Windows partition
2) Make a set of recovery disks in Windows and as Mark pointed out make a repair disk also
3) Install Easus Partition Manager (for Home use) a free download [HERE]("http://www.easeus.com/partition-manager/").
4)With Easus change the HP_Tools partition to  logical (you will have to click apply to confirm action)
5)With Easus,Copy HP_TOOLS partition to  a USB Key formatted to FAT 32. Make sure it remains logical. System  may reboot
6)With Easus delete HP_Tools on your hard drive(making sure that the copy to USB ocurred). System  may reboot
7)Resize the C drive with Easus or Windows Disk management so you have an unallocated space available for Ubuntu ( I would say you need at least 12 GB but I made mine 120 GB). Again you may be asked to reboot.
8)Copy HP_Tools from the USB Key to the new unallocated space with Easus. Make sure you move HP_Tools to the far right side of the unallocated space. Make sure HP_Tools is logical.System  may reboot
9)Using Gparted (You can obtain Gparted separately or use a Live Ubuntu disk and install it temporarily) enlarge Extended Partition(not the HP Tools partition) that is around HP Tools so it encloses all the unallocated space to the left.
10)Using Gparted divide the unallocated space as required for Ubuntu(I used 35 GB for Root, 80 Gb for Home and 6GB for Swap)
11) reboot into Ubuntu Live Disc and install making sure you choose Something else as the install method when asked (otherwise you risk wiping out Windows). Install in the choosen partitions

---

