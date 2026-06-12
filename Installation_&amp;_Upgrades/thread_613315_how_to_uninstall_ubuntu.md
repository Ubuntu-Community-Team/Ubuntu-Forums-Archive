---
title: "how to uninstall ubuntu"
date: 2007-11-14
forum: Installation &amp; Upgrades
---

### Post by Pointswest on 2007-11-14
I have a dell P111 w/  80 g hd.  Dual boot win98se & ubuntu 7.04.  After much difficulty installing 7.04 I now have 3 OS on this machine.  I accidentally installed 7.04 twice so I need to remove it .  I have a new copy of 7.10 I can use if I remove both.  Any help with this would be appreciated as I am new to this but I would really like to make Ubuntu my first choice OS.  I would like to keep the 98 until I learn to use Ubuntu so clear instructions for resizing the partition are needed.

hanks

---

### Post by confused57 on 2007-11-14
You might first want to restore Windows IPL to the mbr, using a Win98SE boot floppy or Super Grub Disk:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

The above probably isn't necessary, but it won't hurt anything to have a boot floppy or SGD.

You should be able to use Gnome Partition Editor in the 7.10 live cd to delete your current Ubuntu partitions and then install Gutsy.

If you want to keep one install of Feisty(the one that works better?), then just install Gutsy over the other install of Feisty...you'd need to select "Manual" partitioning to do this.

You might want to open a terminal and post the output of:
```
gedit /boot/grub/menu.lst
```
menu.lst is short for menu.list

and
```
sudo fdisk -l
```
-l is a small "L"

---

### Post by Pointswest on 2007-11-14
sudo fdisk -l output looks like this:  

disk/dev/sda: 10.2 GB 10254827520
255 heads, 63 sectors/track, 1246 cylinders
units = cylinders of 16065 * 512=8225280 bytes

Device          Boot    Start         End    Blocks                  ID    System
/dev/sda1     *          1             1246   10009463+         c      w95 FAT32 (LBA)

Disk/ddev/sd0: 61.4GB 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
units = cylinders of 16065 * 512 = 8225280 bytes

Device          Boot    Start         End     Blocks                  ID    System
/deb/sdb1     *         1             3666     24947113+         c      win95 FAT32 (LBA)
/deb/d=sdb2           3667        5552     1514295            83     linux
/deb/sdb3                7301       7476     143720                5     extended
/deb/sdb4                5553        7300     14040810          83    linux
/deb/sdb5                7384        7476      746991              82   linux swap/solaris
/deb/sdb6                 7301       7383      666634+           82    linux swap/solaris


I could not attach the Boot/grub/menu.lst and it was too long to manually type.  Hope this might help

---

### Post by confused57 on 2007-11-15
You don't need to try posting your entire menu.lst, just post the lines with title & root, e.g.
```
title		Ubuntu, kernel 2.6.15-29-386
root		(hd0,0)
```

You might want to check out the first 2 links in my signature and the 4th link is the official Ubuntu documentation.   Wouldn't hurt to bookmark these links for future reference.

The Gparted Live CD is an excellent partitioning utility(approx 50 Mb download):
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

I would still recommend downloading & burning a copy of SGD, it's only a 5-7 Mb download.

---

### Post by enemymind81 on 2007-11-15
Easy way is to load the live cd, delete all the partitions on the disc. IF you have a xp/98 disc, you can clear the MBR through the recovery console that way. Boom your done. DBAN is also a nice linux based program which can be run from floppy,usb, or CD. IT wipes your drive with 0's, and more rigrous methods aswell. 

this is how ive done it for a few years with various distros though, there are diffrent and more effecient practical methods to go about this, which im sure others will chime in with.

---

### Post by Pointswest on 2007-11-15
I spent the rest of the evening yesterday trying to use the GParted live cd but I dont think I make a good copy.  The ubuntu CD partitioner seems like it should work.  When I get to the screen with the partitions it looks like this:

Device          Type   Mount point     Format?       Size              Used

/dev/sda       
 /dev/sda1    Fat32   /media/sda1                      10248MB       unknown
/dev/sdb                                                              
 /dev/sdb1    Fat32   /media/sdb1                       30153           866
 /dev/sdb2    ext       /media/sdb2                       15512           2300
 /dev/sdb4    ext       /media/sdb4                       7213             2300
 /dev/sdb7    ext       /media/sdb7                       6802             2200
 /dev/sdb8    swap                                                 361             0
 /dev/sdb6    swap                                                 682             0         
 /dev/sdb5    swap                                                  764            0


There is also a message at the bottom of the window that says:  You need to specif a partition for the root file system (mount point "/") with  a minimum size of 2 GB, and a swap partition of at least 256MB.

I think there used to be a partition called /dev/sdb3 and I accidently deleted it.


Results of  /boot/grub/menu.lst show:

Title windows 95/98/nt/2000
root  (hd0,o

title     linux
root(hd0,1

After a line called  End debian automatic kernels list it shows the following:

           Title                                        root

win/95/98/me                                   (hd0,0)
win/95/98/me                                   (hd1,0)

Ubuntu ,kernel 2.6.20.15                 (hd1,1)
  generic (on /dev/sdb2)               

Ubuntu,kernel 2.6.20-15-                 (hd1,1)
 generic recovery mode
(on /dev/sdb2)

Ubuntu memtest 86+                          (hd1,1)
(on /dev/sdb2)

Ubuntu, kernel 2.6.20-15-                    (hd1,3)
generic (on /dev/sdb4)

Ubuntu ,kernel 2.6.20-15-                     (hd1,3)
generic (recovery mode)
(on /dev/sdb4)

Ubuntu, memtest86+                           (hd1,3)
(on /dev/sdb4)

---

### Post by confused57 on 2007-11-15
I see that each of your hard drives have a FAT32 partition at the beginning...which one is your Win98 install?

My recommendation would be to download & burn a copy of the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
after you download the iso, use your cd-writing software to burn the iso as an "image"(not as a data or bootable cd), burn it at 8x or less.

After you've burned the SGD cd, boot up your computer with the cd inserted...there are instructions in the above link for repairing your Windows mbr...look for an option something like "Fix Boot of Windows".   SGD can also boot Windows and Ubuntu, if you have any problems.
OR, if you already have a Win98SE boot floppy you can boot this & enter:
```
fdisk /mbr
```
this will also repair your mbr, but SGD is a handy utility to have for booting problems

The reason I'm suggesting this is that once you're able to boot Windows from the Windows IPL on your mbr, you should be able to delete all your linux partitions, then reinstall Gutsy or Feisty.

If your first hard drive is where Win98 is installed & you're able to repair the mbr(and you don't mind opening your computer & switching the drives), you might want to consider this option:
[http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

I was pretty clueless myself when I first installed Ubuntu(my first experience with linux), however I took the easy route and selected to use the entire disk(overwriting a Win98SE install).

---

### Post by Pointswest on 2007-11-16
I assume these fat32 partitions are from my win os.  When I added the 60 gb hd I used a program from maxtor to move all the win files to the new disc but it would not move the win98 os .  I guess  that  is why the fat32 shows up  on both  discs.

I haven't been too successful burning these iso files but I will try your suggestion of the super grub disc.  What is windows mbr?  If I can't fix this soon I think you are right to just save what I want from win on another machine and do a clean installl.  Sorry I have to ask so many questions but I am way over my head right now.  I think i might have deleted a partition this morning called /dev/sdb3.

---

### Post by confused57 on 2007-11-16
> **Pointswest said:**
> I assume these fat32 partitions are from my win os.  When I added the 60 gb hd I used a program from maxtor to move all the win files to the new disc but it would not move the win98 os .  I guess  that  is why the fat32 shows up  on both  discs.

I haven't been too successful burning these iso files but I will try your suggestion of the super grub disc.  What is windows mbr?  If I can't fix this soon I think you are right to just save what I want from win on another machine and do a clean installl.  Sorry I have to ask so many questions but I am way over my head right now.  I think i might have deleted a partition this morning called /dev/sdb3.
Here's an excellent explanation of the mbr:
[http://users.bigpond.net.au/hermanzone/p6.htm](http://users.bigpond.net.au/hermanzone/p6.htm)

I was referring to reinstalling Windows IPL to the first hard drive's mbr...this should allow you to boot into Win98 the way you did before installing Ubuntu.  This way, you can delete all the Ubuntu partitions and still be able to boot Windows.  Then you can determine how you want to partition your disk(s) for  an Ubuntu reinstall.

I believe in Ubuntu, you can just right-click on the iso and this will write it as an image to a cd...If you're burning the iso on another pc with Windows, the cd burning software(Roxio, Nero, etc) should have an option to burn it to disk as an image.

There is definitely a learning curve for Ubuntu & linux and the best way to learn is by doing...I usually learn the most when I make mistakes & have to troubleshoot or search the forum(or Google).  Hang in there, it's really not as difficult as it seems.

---

### Post by Pointswest on 2007-11-17
I am still having trouble opening these iso downloads.  Am going to try and find my 98 boot disc and try that method.  I was able to use the GParted program on the 7.10 disc to delete all but my win 98 and the new copy of 7.10.  Now when I click on the items in the grub menu the deleted ones say no partition.  

How can you remove the unwanted entries from the grub menu.

---

### Post by confused57 on 2007-11-17
> **Pointswest said:**
> I am still having trouble opening these iso downloads.  Am going to try and find my 98 boot disc and try that method.  I was able to use the GParted program on the 7.10 disc to delete all but my win 98 and the new copy of 7.10.  Now when I click on the items in the grub menu the deleted ones say no partition.  

How can you remove the unwanted entries from the grub menu.
If you have a working dual boot with Win98 and Ubuntu 7.10, you don't really need to restore Windows IPL to the mbr.

You can remove the grub references to the deleted partitions, by opening a terminal:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```
For now you can just place a #(comment out) the entries that don't work...if your system boots OK, then you can delete the entries.

Are you able to boot into 7.10, without any problems?  If not, you probably need to edit your /etc/fstab to remove references to the deleted partitions that fstab is attempting to mount.
```
sudo cp /etc/fstab /etc/fstab_backup
gksudo gedit /etc/fstab
```

The above commands will work on your installed Ubuntu 7.10...you can use the live cd, but you'll need to mount your root partition first.

You might want to repost the output of:
```
sudo fdisk -l
```

Added:  Here's a link describing how to mount your root partition:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)
If you have problems with mounting, post your fdisk -l & I'll try to guide you through it...describe any error messages you're getting trying to boot 7.10.

FYI, here's a guide for fstab:
[http://ubuntuforums.org/showthread.php?t=283131&highlight=fstab](http://ubuntuforums.org/showthread.php?t=283131&highlight=fstab)

Partitioning:
[http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)
[http://www.users.bigpond.net.au/hermanzone/p17.htm#help_on_partitioning](http://www.users.bigpond.net.au/hermanzone/p17.htm#help_on_partitioning)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by Pointswest on 2007-11-21
After struggling for several days with these iso files I have now run the SGD program .  I was not having any problem booting win or  7.04 before this.  After deleting some of the partitions and loading 7.10 my sudo fdisk-l output looks like this:

Disk/dev/sda :10.2GB  10254827520
255 Heads, 63 sectors/track, 7476 cylinders
Uniys = cylinders of 16065 * 512=8825280 bytes
Disk identifer : 0x0000001

Device    Boot  Start       End             Blocks      ID     System

/dev/sda   *     1        1246           10008463+     C    w95fat32(LBA)


Disk/dev/sdb : 61.4GB 61492838400 bytes
255 heads, 63 sectors/track,7476 cylinders
Units = cylinders of 16065 * 512 =8225280 bytes
Disk identifier 0x00000000

Device         Boot     Start     End     Blocks            Id   System

/dev/sdb1    *           1         3193    25647741     C    w95FAT32 (LBA)
/dev/sdb2                 3194   6336    25246147+   83   linux
/dev/sdb3                 6337    7476    9157050        5    extended
/dev/sbd5                  7384   7476        746991     82   linux swap/Solar
/dev/sbd6                 7301    7383   666634+       82   linux swap/solari
/dev/sdb7                 6430    7256   6642814+    83    linux
/dev/sbd8                 7257    7300    353398+      82  linux swap/solar
/dev/sdb9                 6337    6429    746959+      82  linux swap/soalri
 
Disk/dev/sdc : 65 Mb -------Bytes
16 Heads,32 sectors/track, 250 cylinders
Units = cylinders of 512 = 26214 bytes
Disk identifier 0x00000000

Device           Boot  Start    End   Blocks                 Id      System

/dev/sdc1      *       1       249      63728                6       FAT16


Now my grub shows two ubuntu kernels and one 98se OS.  Now that I have installed the 7.10 version I shouldn't need the 7.04 version any more so I wilttry again to delete the 7.04 with the GParted program  I would really like to run the 98se on the 10G drive and ubuntu on the 60G drive but I am afraid of messing up.  The GParted disk has no help files so I am pretty lost.

---

### Post by mikewhatever on 2007-11-21
Not sure what the help file is for, but here is an alternative [http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

---

### Post by confused57 on 2007-11-21
See the link mikewhatever posted...here's some screenshots(also see the resizing link):
[http://gparted.sourceforge.net/larry/livecd/livecd.htm](http://gparted.sourceforge.net/larry/livecd/livecd.htm)

I assume you were able to successfully burn the SGD iso and boot to it by restarting your pc with the cd inserted...Have you tried booting your Win98SE, using SGD?  If you can, I would recommend using the Gparted live cd or Gnome Partition Editor on the Ubuntu live cd, then deleting all of your linux partitions and reinstalling Ubuntu 7.10.  I believe if you selectively delete partitions, it may render 7.10 unbootable, which can be fixed, but it would "tidy" up your 2nd hard drive by doing a clean install.

With Gparted, you would just click on the partition you want to delete, then click on Partition in the top menu, select "delete"...you'll be asked to confirm, then the task will be added to queue, then click "Apply".
You could do one partition at a time or add them all one at a time to the queue, then click Apply.

Then do a clean install of 7.10 on the unallocated space(free space) of your 2nd hard drive.

If SGD is working OK to boot your Win98SE, you should be able to repair the 1st hard drive's mbr to boot Windows, if something goes wrong.  It's the way I would proceed if it were my pc...you may want to wait to see if anyone has a better suggestion.

---

### Post by Pointswest on 2007-11-22
I have   used the GParted disk to remove all partitions associated with linux, then ran the boot disk from super grub disk to restore the normal win boot.  Then installed Ubuntu 7.10  to the second  hard drive.  now everything is working as expected from the dual boot.  I can't thank everyone enough for their input.  Now if I can just get my wireless working I will be thrilled to start using Ubuntu.

Thanks for all the help

Pointswest

---

