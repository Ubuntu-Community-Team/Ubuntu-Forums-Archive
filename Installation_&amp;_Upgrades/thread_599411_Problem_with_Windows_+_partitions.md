---
title: "Problem with Windows + partitions"
date: 2007-11-01
forum: Installation &amp; Upgrades
---

### Post by Virgofenix on 2007-11-01
Am trying to configure the ff setup:
(all sizes approximations)

MaxtorHD:

Partition1 40GB -- Windows XP <--- NTFS formed from XP install

SeagateHD:

Partition2 30GB -- ext3 home
Partition3 37GB -- ext3 Linux
Partition4 1GB -- swap
Partition5 165GB -- NTFS storage <-- formed using Gparted

Problem:

Linux was installed first, and the NTFS storage in partition5 was made using Gparted. Freshly installed Windows in partition1 isn't recognizing partition5 ntfs. In Windows, apart from the Windows drive(let's label as drive C, for convenience), I am given the option to format a drive with 131GB(let's label as drive F).

I am guessing there's something wrong with the mbr.

---

### Post by Pumalite on 2007-11-01
1.-Windows has to be installed first
2.-install Grub to MBR when you install Ubuntu and you'll have a menu to dual boot.

---

### Post by Pumalite on 2007-11-01
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)

[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)
Here's a link explaining configfile entries:
[http://users.bigpond.net.au/hermanzo..._Linux_Systems](http://users.bigpond.net.au/hermanzo..._Linux_Systems)
[http://users.bigpond.net.au/hermanzone/p15.htm#menu.lst](http://users.bigpond.net.au/hermanzone/p15.htm#menu.lst)

---

### Post by Virgofenix on 2007-11-01
My problem is that Windows can't recognize the space in my second hard drive. Windows says that it is a 131GB hard drive - while it has a capacity of 250 and none of the partitions are at 131GB.

BTW, I cannot delete my Linux partitions as they contain important data; so the option of formatting everything is out (I have files several GB worth).

---

### Post by Pumalite on 2007-11-01
To view Linux partitions from Windows:

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by Virgofenix on 2007-11-01
I will try to clarify:

Windows sees my Seagate harddrive as only having 131GB.

131GB is not the maximum capacity of my seagate harddrive. None of the partitions on my seagate harddrive is 131GB.

I don't know how Windows sees the sizes of other drives. I don't know how MBR functions. Does it have something to do with how much space Windows sees? I do not wish for Windows to see my Linux partitions.

---

### Post by Pumalite on 2007-11-01
Did you install Ubuntu?. Do you wish to install Ubuntu?. Otherwise, I don't understand.

---

### Post by meierfra on 2007-11-01
Can you access "partition 5" from ubuntu? What is the output of "sudo fdisk l"?

---

### Post by Virgofenix on 2007-11-02
> **Pumalite said:**
> Did you install Ubuntu?. Do you wish to install Ubuntu?. Otherwise, I don't understand.

Ubuntu has already been installed.

I'm going to start from the beginning:

Previously, my partitions were:
(all sizes are approx.)

MAXTOR(40GB):

30GB NTFS (storage) - A
7GB NTFS (Windows) - B

Seagate(250GB):

190 GB - NTFS (storage) - C
40GB ext3 - Ubuntu -D
1GB swap - E

This setup wasn't very convenient as my Windows partition was nearly using all of the space allocated for it; and hence, being forced to compress and decompress far too often. Further, I wanted to create a /home folder for Ubuntu, to help upgrading.

Hence, I tried to create the setup listed in my first post.

Steps I took:

1)I copied the contents of A to C. 
2)I deleted A and B and combined them together (F). 
3)Formatted F to an ext3 and put all my files there from C.
4)Formatted C.
5)Created a 30GB /home ext3 partition(G - 30 GB from the unallocated space created from C's deletion).
6)Transferred my files from F to G and D.
7)Deleted the F.
8)Installed Windows in the unallocated space created by F..
9)Made an NTFS partition out of the remaining space from deletion of C.

Now, the current problem:

The NTFS partition I made using Ubuntu isn't being recognized in Windows. Yes, it can be mounted on Ubuntu.

Windows sees the other drive as an unformatted 131GB of space. The maximum capacity of my Seagate HD is 250 and none of my partitions are 131GB.

fdisk:

hda(MAXTOR):

The number of cylinders for this disk is set to 4866.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Disk /dev/hda: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4865    39078081    7  HPFS/NTFS

hdb(Seagate):

The number of cylinders for this disk is set to 30401.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        3875    31125906   83  Linux
/dev/hdb2   *       25497       30279    38419447+  83  Linux
/dev/hdb3           30280       30401      979965   82  Linux swap / Solaris
/dev/hdb4            3876       25496   173670682+   5  Extended
/dev/hdb5            3876       25496   173670651    7  HPFS/NTFS


I do not know how mbr functions, but I'm guessing it's part of the problem.

---

### Post by Pumalite on 2007-11-02
Is it /dev/hdb5 that you cannot see from Windows?

---

### Post by Virgofenix on 2007-11-02
^Yes.

I read that Windows can only see 4 partitions max?

---

### Post by Pumalite on 2007-11-02
Yes. A maximum of 4 primary partitions. So you have to get to three and from there get an extended partition and in there you can make several logical partitions.

---

### Post by Virgofenix on 2007-11-02
Yes, regarding that:

Device Boot Start End Blocks Id System
/dev/hdb1 1 3875 31125906 83 Linux                                           - primary
/dev/hdb2 * 25497 30279 38419447+ 83 Linux                             - primary (home)
/dev/hdb3 30280 30401 979965 82 Linux swap / Solaris             - primary
/dev/hdb4 3876 25496 173670682+ 5 Extended                           - logical
/dev/hdb5 3876 25496 173670651 7 HPFS/NTFS                          - logical

Can /home be just a logical partition?

So, please check me on this, I have 4 primary partitions: 

ext3 Linux
Windows NTFS
ext3 /home
swap

I need to remove one to have Windows see the NTFS logical partition?

---

### Post by Pumalite on 2007-11-02
Yes. Ubuntu is fine working with logical partitions, whereas Windows requires primary partitions.

---

### Post by Virgofenix on 2007-11-02
Can /home be just a logical partition?

Can I get explanation as to why Windows is seeing a drive in my Seagate with 131GB of unformatted space?

---

### Post by Pumalite on 2007-11-02
Post:
sudo fdisk -lu

---

### Post by fdv1 on 2007-11-03
This is a Windows question, so I'll answer as best I can.

Does your motherboard have built-in mirroring in the IDE controller you have the big NTFS drive plugged in to?

Here's why I ask.

You're in Linux. You have your new big hard drive plugged into a controller. The controller happens to be RAID. Linux thinks it is making one volume of a set, and creates an NTFS volume... that Windows (improperly) sees as part of a RAID configuration.

I sketch this scenario because this same exact thing happened to me, but I had the benefit of a strong index of suspicion and a BartPE recovery disk with Partition Manager on it, which showed NTFS... and in Windows 2000, the volume manager showed one drive in a RAID 0 configuration. I was frantic, as Windows kept offering to format it, saying it didn't recognize it... yet it was NTFS!

Anyway, let me know. Generally speaking it is better to create NTFS volumes with Windows if Windows is going to be on the same system. Call me superstitious, that's all.

---

### Post by Virgofenix on 2007-11-03
It does not have any RAID options. It's a relic from 2002.

However, Windows previously saw an NTFS partition in my Seagate 250GB harddrive. The partition *was* created in Windows. I can't quite remember if it was logical or primary. Anyway, when I reinstalled Windows, it could no longer see the same NTFS partition.

Can you elaborate more on:

"Linux thinks it is making one volume of a set, and creates an NTFS volume... that Windows (improperly) sees as part of a RAID configuration."

I'm not too knowledgable abour RAID, unfortunately.

sudo fdisk-lu:

Disk /dev/hda: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders, total 78177792 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63    78156224    39078081    7  HPFS/NTFS

Disk /dev/hdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1              63    62251874    31125906   83  Linux
/dev/hdb2   *   409593240   486432134    38419447+  83  Linux
/dev/hdb3       486432135   488392064      979965   82  Linux swap / Solaris
/dev/hdb4        62251875   409593239   173670682+   5  Extended
/dev/hdb5        62251938   409593239   173670651    7  HPFS/NTFS

I appreciate the help so far.

---

### Post by Pumalite on 2007-11-03
Get a Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)
Boot from it and examine your Seagate for 'hidden partitions' or 'unallocated space'. I doubt you'll find any. I think is a Windows thing. Did you install the driver I gave you, in Windows?

---

### Post by Virgofenix on 2007-11-03
> **Pumalite said:**
> Get a Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)
Boot from it and examine your Seagate for 'hidden partitions' or 'unallocated space'. I doubt you'll find any. I think is a Windows thing. Did you install the driver I gave you, in Windows?

No. Like I said, I don't want Windows to see my Linux partitions.

What's the difference between the Gparted Live CD and the GNOME Partition Editor inside Ubuntu? 

I'll try to find a way to backup my data and just reformat all my drives, though I'll look at this as a last resort. I also think that this is a Windows issue. I've got a hunch it has something to do with the mbr. Thanks, anyway, a lot for the help. I'm still open for other suggestions.

---

### Post by Virgofenix on 2007-11-11
I just found the problem.

I suffered a lot of freezes with Feisty, and had to do a lot of hard resets. Apparently, my Seagate has labaled about half of its space as logical bad sectors.

Any suggestions?

---

### Post by Virgofenix on 2007-11-12
Bump.

Please help.

---

