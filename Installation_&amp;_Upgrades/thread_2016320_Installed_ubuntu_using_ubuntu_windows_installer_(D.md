---
title: "Installed ubuntu using ubuntu windows installer (DOESNT BOOT UP)"
date: 2012-07-04
forum: Installation &amp; Upgrades
---

### Post by lukem on 2012-07-04
I have a similar problem.  

Brand new lenovo with windows home premium and I did the ubuntu (windows) install.  I think it was wubi.  Everything worked fine for a couple of days and I decided to set up a shared directory in ubuntu.  It loaded samba for that purpose and said to reboot.  I chose reboot but was not around to make it reboot into ubuntu and it came back up in windows instead.  

Now when I reboot I get a screen to choose Win7 or ubuntu but ubuntu will not work.  I get the purple screen with the dots but it goes no farther.  Win7 will boot OK.  I loaded some photos in ubuntu that I no longer have access to and really want to copy them to a safe location before I try a fresh install.  

Thanks for any help you can provide.

---

### Post by coffeecat on 2012-07-04
Move to own thread.

@lukem, the OP of the thread you posted to was using the developer version of Windows 8 which may be a consideration. It is better to start your own thread.

---

### Post by msammels on 2012-07-04
I heard Wubi has problems, because of the System partition and the manufacturer's partition. Does GRUB give any errors?

---

### Post by lukem on 2012-07-04
Thanks Coffee Cat

No error message of any kind.  

Thanks to all for your help.

---

### Post by lukem on 2012-07-04
Read the Wubi Wiki.  It suggested 3 tools to read the linux files from Win, but none of them work on Win7.  I tried running chkdsk /r then rebooting.  
When I tried to boot ubuntu it did give me a command line prompt GRUB> but I didn't know what to type there.  
Appreciate any help.

---

### Post by lukem on 2012-07-04
I found an article on grub that said you could tell it partition name and the kernel location  then issue the boot command using a built in "FIND" function, but when I tried it the response was "Unknown command FIND".  

Still hoping to be able to boot this partition and save the files stored there.

---

### Post by lukem on 2012-07-06
Tried something I found elsewhere using a 12.04 install disk to do the trial install:


ubuntu@ubuntu:~$ sudo fdisk -l
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x73b51f70

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2   *      206848  1900941311   950367232    7  HPFS/NTFS/exFAT
/dev/sda3      1900941312  1953525167    26291928   12  Compaq diagnostics
ubuntu@ubuntu:~$ sudo mkdir /win
ubuntu@ubuntu:~$ sudo mount /dev/sda2 /win
ubuntu@ubuntu:~$ sudo mkdir /vdisk
ubuntu@ubuntu:~$ sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk
mount: /dev/loop1: can't read superblock

It was supposed to mount it so I could save files, but got this instead.  Any ideas?  
Thank you
Luke

---

### Post by oldfred on 2012-07-06
I do not know wubi, but it sounds like it needs the Linux version of filecheck - fsck or e2fsck. 

sudo mkdir /media/win
sudo mount /dev/sda2 /media/win
sudo fsck /media/win/ubuntu/disks/root.disk
Then check if you can mount it & read it:
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt

---

### Post by cbennett926 on 2012-07-06
I would try and load up a LIVE CD/USB while the hard drive is connected (I say that because out of precation I never use a LIVE while my harddrive is connected) and try and access the file. Also, if you are trying to get to one file within Ubuntu, you can click Start --> Computer --> Click on computer --> Click program files (there might be x86 or a plain program files) --> Check if there is an Ubuntu directory and the files should be located where you put them within there!

---

### Post by lukem on 2012-07-07
Thank you very much for your replies.

oldfred, I was not able to mount it so I guess fsck will not help me.

cbennett926, I used a live CD go get what I posted in the last post.  There are no files in the explorer.  

In windows the rootdisk says zero KB.  I think I have lost all possibility of mounting it.  I may need to look for more basic ways of retrieving the data.  Disk seems OK but looks like files have been deleted.

---

### Post by lukem on 2012-07-08
Ran Test Disk using Ubuntu Live CD. Ran Scan and got the following:

TestDisk 6.13, Data Recovery Utility, November 2011
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 1000 GB / 931 GiB - CHS 121602 255 63
     Partition               Start        End    Size in sectors
 * HPFS - NTFS              0  32 33    12 223 19     204800 [SYSTEM RESERVED]
>D HPFS - NTFS             12 223 20 118328  31 39 1900734464
 D HPFS - NTFS           4811 174 36  6724  11  7   30722048 [WFTWINPE]
 P HPFS - NTFS          118328  31 40 121591 202 19   52430848 [LENOVO_PART]


Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
NTFS, 973 GB / 906 GiB

Is it possible to Undelete the deleted partitions  I couldn't find a way to do it with this utility.  Any help would really be appreciated.

---

### Post by oldfred on 2012-07-08
I do not think testdisk can recover wubi. Wubi is just a file inside the NTFS partition and relies on Windows to boot and NTFS to support the file. Testdisk restores partitions and may find files inside deleted partitions. If NTFS partition has issues it may then damage the wubi install. Windows chkdsk may have moved the file to a chkdsk folder?

If you like Ubuntu & are willing to partition then it may be time to move to a full partitioned install. wubi is fine for testing but not as reliable for long term use.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn&#8217;t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

---

### Post by lukem on 2012-07-08
I've been running ubuntu on a dedicated partition since the whart hog days.  I don't tend to keep up with new developments until I get a new pc and need to do a new install.  This time Wubi was really out front seemed to be the version that was being promoted so that is the only reason I chose it.  I will do a regular dual boot as soon as I can either recover these family photos or give up and decide they are lost on this disc and I will never be able to get to them.

The windows based utility I ran found thousands of deleted images (mostly .pngs) but none of the photos I put into the ubuntu section.  I guess I need to go back to searching with windows utilities instead.

---

### Post by ekymz on 2012-07-09
> **lukem said:**
> I've been running ubuntu on a dedicated partition since the whart hog days.  I don't tend to keep up with new developments until I get a new pc and need to do a new install.  This time Wubi was really out front seemed to be the version that was being promoted so that is the only reason I chose it.  I will do a regular dual boot as soon as I can either recover these family photos or give up and decide they are lost on this disc and I will never be able to get to them.

The windows based utility I ran found thousands of deleted images (mostly .pngs) but none of the photos I put into the ubuntu section.  I guess I need to go back to searching with windows utilities instead.

hello, i am new member here, but i think window based system may not  find the photos you are looking for, if you have assigned your folder  for ubuntu which are set to private, windows will not look at it.  correct me if i am wrong in this issue, but usually, windows based system will not look at the folders that is hidden until you tell it to do so. try showing all the hidden folders instead and search it manually.

and for wubi, try rebooting up again, then when it comes to the selection of OSs, select Ubuntu and press F8, it will direct you to recovery mode, from there select what you want to do, upgrade GRUB or repair your ubuntu, and have your live cd with your side,you may be needing it, i don't guaranty that it will work but try it. ;)

---

