---
title: "Partitionning options for terabyte hard disks"
date: 2008-11-11
forum: Installation &amp; Upgrades
---

### Post by damien.depluvrez on 2008-11-11
Hello everyone, 

I just finished refreshing one of my machines with a clean install of Ubuntu Server 8.10 (x86-64), to act as a Samba file server.
Everything goes well during installation, like a breeze ;), and the server boots fine once set up.

I've got a question regarding the partitionning of the data disks I use.
These are Hitachi 7K1000 1TB SATA drives.  There are 4 of them, each containing a single primary partition of 1TB.
These are used solely as data drives under /mediadisks, the /, swap  and /home are on another disk.

If I partition these drives on Mac OS X Leopard using Disk Utility, and format them as HFS+, the formated capacity comes about roughly 931GB, which is the normal formatted capacity for such drives.

If I use the partitionner that runs when installing Ubuntu Server, (i believe it's called partman, not sure about that), choosing 'Manual' and selecting the following options : 
 
- Create a single 1TB primary partition
- format it as a ext3 FS
- Mounting it under /mediadisk with these options : noexec, nosuid, noatime
- with 0% reserved blocks for the super-user (this disk will only be used for data)
- Setting the usage parameter to 'standard'

Then when the system is installed, issuing a **df -h** shows me : 
```
/dev/sdb1           917G  200M  917G    1%    /mediadisk
```

Or, using **df -H** (mind the case) :
```
/dev/sdb1           985G  200M  985G    1%    /mediadisk
```

Thus my 1TB disk has lost some 25GB somewhere when being formatted ?! :confused:
But wait, there is more !

If I re-run the installation, and choose the following options when partitionning the drive (what has changed is in bold): 

- Create a single 1TB primary partition
- format it as a ext3 FS
- Mounting it under /mediadisk with these options : noexec, nosuid, noatime
- with 0% reserved blocks for the super-user (this disk will only be used for data)
- **Setting the usage parameter to 'largefile'**

In this case, once the system installed, a **df -h** says : 
```
/dev/sdb1           932G  200M  932G    1%    /mediadisk
```

Or, with **df -H** : 
```
/dev/sdb1           1.0T  200M  1.0T    1%    /mediadisk
```

Thus this **largefile** option during formatting allows me to use the full capacity of my disk, namely 932GB.
I get the same capacity as if it was formatted using another system (e.g. Mac OS X Leopard as HFS+, or even Windows XP as NTFS)

The same problem exists when I want to partition and format the backup disk (Same 1TB drive, this time in a external USB2.0 enclosure), 
using the classic procedure fdisk / mkfs -t ext3 -m 0 / mount, the now mounted backup disk says it only has 917GB available.

Is there a way to tell fdisk (or mkfs) to switch in **'largefile'** mode, as the partitioner used during install, and the reclaim those lost 25GB ?

Any help appreciated !

---

### Post by Pumalite on 2008-11-11
1 gb=1024 mb

---

### Post by damien.depluvrez on 2008-11-11
> **Pumalite said:**
> 1 gb=1024 mb

Yeah, I still know my binary ;)

That's why i posted the output of df -**h** and df-**H** : the first outputs in powers of 2, the other one in powers of 10.

As you can see, 932GB (powers of 2, *classic good ol' binary* : 1GB = 1024MB) corresponds to 1TB (powers of 10, *marketing speech* : 1GB = 1000MB), 

but 917 binary Gigabytes sitll gives me 985 marketing Gigabytes ;)

The thing i'm puzzled with is how the '**largefile**' usage parameter affects the formatted capacity.
I'm prety sure it has to do with inodes or something like that, but how can I tell fdisk or mkfs that it's this 'largefile' mode I want to work with ?  I searched in forums, even manpages, but found nothing ...

---

### Post by damien.depluvrez on 2008-11-23
So, I finally found how that 'largefile' option affects the file system 8). 
it's the mkfs.ext3 -T option, and yes it has to do with inodes.
As I understand, the inode_ratio (amount of MB per inode) is set much higher, thus creating less inodes and therefore leaving more capacity to the disk, rather than using that space to create inodes.

---

