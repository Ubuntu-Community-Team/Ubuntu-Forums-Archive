---
title: "Partitioning during installation"
date: 2010-04-01
forum: Installation &amp; Upgrades
---

### Post by diego_pmc on 2010-04-01
Hello everyone,
I am a Windows user and lately I have been running Linux from CD in order to get used to its interface. I've tried installing it, but I have some difficulties with partitioning.

I've partitioned the hard drive many times before (in Windows installation). I'm having problems with all the different types of "Use as" and "Mount point" -- I don't know which to choose and why.

I've found a [tutorial on Softpedia](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml) which explains how to create a swap area partition, and all the rest, but I'm still a bit confused.

This is how I want to partition my drive:
Total size: 160 GB
Ubuntu: 30 GB
Windows XP: 30 GB
Others: 100 GB 

Could you please give me some details as to how to do this and also why I need a swap area, what the partition with the "/home" mount point is used for, etc.?

---

### Post by dstew on 2010-04-01
If you are used to Windows partitioning, you may find some aspects of partitioning for Ubuntu confusing. This is because with Windows, some of the details are hidden. Remember that in Windows, partitions used to be called "disks", without reference to partitions or file systems.

In Ubuntu (and Linux in general) the vocabulary used is different, and I think more precise. Technically, a partition is just a space on the disk set aside for something. A partition can be truly empty (contains random bits), but usually we put a file system into a partition. The file system may or may not fill the whole partition, but usually it does. A Windows "disk" is really a partition that contains a Windows file system.

In an Ubuntu system, there are two types of "partitions", but really they are different types of file systems within partitions (remember the partitions themselves are just containers). The main file system has the type ext3 or ext4. It is designed to contain files, just as the Windows files system. It has a different structure, however, and needs the Linux software to read it. Windows does not attempt to use ext3 or ext4 file systems. Linux, however, can use Windows NTFS file systems.

The other type of "file system" is really not a file system in the traditional sense. This is the swap space. It does not have directories and files in it. It is used by the Linux operating system to temporarily store memory. I don't know much about the details of how swap works, but basically it just holds memory image data for later use. In Windows, this same function is done by "Virtual Memory". You might recall that in Windows you can create a separate file for this, called a pagefile.

So, when partitioning in Linux, you set aside a partition for the main file system, formatted as ext3 or ext4, and a partition for swap space. Since there is no file system in the swap space, you just designate the partition as "use as swap" and do not format it.

In Linux, devices such as file systems are mounted on the directory tree at "mount points". You create a mount point (which is the same as creating a directory), then "mount" a file system to it. It comes from the old terminology of mounting tapes on tape drives. The main file system has the default mount point of '/' (without the single quotes). This mount point or directory is called "root". All other file systems and devices are mounted under this directory. So, the installer needs to know which file system will be designated as root (given the mount point '/', without the single quotes). The root file system has to be formatted as ext3 or ext4.

You do not need to designate a separate partition as swap space. If you don't, the Linux system will just create a file to do swapping. However, it is generally thought that having a separate partition, of the same size as your memory, will make the system faster. You also do not need to designate a separate partition for /home if you don't want to. The installer will create a /home directory under the / directory in the root file system. Some people like to create a separate /home partition, because if you upgrade by installing another Linux system, you can use the same /home partition, which contains your documents.

---

### Post by oldfred on 2010-04-01
If a disk drive is a file cabinet then the drawers are the partitions. Files and folders are in the partitions.

When originally designed you could only have 4 partitions under the standard MBR partition scheme. It was later modified where one of the four 'primary' partitions could be converted to an extended partition and hold additional 'logical' partitions. Windows must have a primary partition for booting, linux works fine from logical and windows data can be in logical partitions.

For three years I had windows, linux root, swap and a small (20GB)  shared partition for data used by both windows & linux like my firefox and thunderbird profiles.

Swap is memory overflow space, windows has the same thing but as a file inside its 'root' or operating system partition. When RAM memory was only 256M swap was sized at 2 times memory. Now I recommend 2GB or the same size as RAM unless you have a very small hard drive. The only reason for larger is is you want to hibernate as with systems today have larger RAM. Only loading many or a few very large programs will ever cause swap to be used.

Separate /home makes it easy to upgrade to a new version as all your files and settings are in /home. Since I want to have several system installs I also made a separate /data so my current root is 5GB, my /home is 1GB, my swap is 4GB (size of RAM) and I have large data files in other linux partiion(s) or shared NTFS partitions. I have to agressively create or move data from /home to data folders in my data partitions since a lot of data is normally stored in /home.

More info on partitions.
(I do not recommend FAT anymore) but good info:
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

If you have a separate /home and/data in other partitions, your root (/) only needs to be 10-20GB.

---

### Post by dabl on 2010-04-01
I have always found it easier to treat the disk partitioning as a separate (predecessor) activity to installing the OS.  Most Linux distributions do incorporate a partitioner and offer to do that at the beginning of installation, but it seems to me just to make a fairly intense project even more complicated, especially for the inexperienced folk.

So, I recommend you download and burn either a Parted Magic Live CD from here:  [http://partedmagic.com/download.html](http://partedmagic.com/download.html)

or a GParted Live CD from here:  [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

The Parted Magic CD has some additional cool features, including CPU benchmarking and disk testing utilities.

So, use the partitioning CD to do your hard drive partitioning.  Then you can use the *buntu Alternate Install CD to do your OS installation, choose "manual" partitioning, and all you have to worry about is selecting the correct partition on which to mount the filesystems.  No changes to the partitioning are needed. ;)

---

### Post by dstew on 2010-04-01
@dabl: I agree with you. I usually partition ahead of time.

---

### Post by diego_pmc on 2010-04-02
Many thanks to all of you for the help and the explanations. I managed to partition the drive the way I wanted to, but now I need help with a few other things:
• [Ubuntu cannot connect to the Internet]("http://ubuntuforums.org/showthread.php?p=9064523#post9064523")
• [How to have less boot options?]("http://ubuntuforums.org/showthread.php?p=9064533#post9064533")

---

### Post by Mark Phelps on 2010-04-02
Please start new threads for your new problems -- since they have nothing to do with partitioning.

---

### Post by dstew on 2010-04-02
Mark, he already did. Those questions are links to new threads.

---

