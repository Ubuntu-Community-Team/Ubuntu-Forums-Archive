---
title: "Dual Boot"
date: 2014-01-20
forum: Installation &amp; Upgrades
---

### Post by Joe_Ciaravino on 2014-01-20
Hello all. I'm new here and have a newbie question:

I'm building a new machine using a 256 gb SSD and a 256 gb 7200 RPM  HDD. I'm installing Windows 7 64 bit and UBUNTU 12.4 64 bit for dual  boot capability.

  
 I'd like to partition the SSD and use it to install Win 7 and all  system/program files on 1/2 and UBUNTU and all related programs on the  other 1/2, and use the SSHD for all documents, pictures, videos and  music accessible to both OSs. Id this possible?
  
 Thanks in advance.

---

### Post by Mark Phelps on 2014-01-20
If you install Win7 on a bare drive, by default, it will create two partitions -- a boot partition and an OS partition.  Unless you are planning on encrypting your Win7 install, this is needless.  So instead, you should create the NTFS partition for Win7  before you install it.  One way to do this would be to use the Live Ubuntu media and GParted on that, to create an empty NTFS partition. Then, when you boot using the Win7 install media, be sure to use the option to reformat the partition.

Then, boot from the Ubuntu install media, use the "something else" option and create the partitions needed.  You only really need two: Root and Swap.

---

### Post by oldfred on 2014-01-20
On my 64GB SSD I have two Ubuntu installs of 28GB each. I would think it better in your case to make Windows system partition larger and Ubuntu root partition smaller.

Then you can have a larger NTFS shared data partition on the rotating hard drive.

I use two shared data partitions one NTFS and one Linux formatted. I now have stopped using XP but have not yet converted/reconfigured data in NTFS partition into Linux data partition. I link all data back into /home and have used about 11GB of / (root) including my /home on my working install.

---

### Post by Joe_Ciaravino on 2014-01-20
> **oldfred said:**
> On my 64GB SSD I have two Ubuntu installs of 28GB each. I would think it better in your case to make Windows system partition larger and Ubuntu root partition smaller.

Then you can have a larger NTFS shared data partition on the rotating hard drive.

I use two shared data partitions one NTFS and one Linux formatted. I now have stopped using XP but have not yet converted/reconfigured data in NTFS partition into Linux data partition. I link all data back into /home and have used about 11GB of / (root) including my /home on my working install.

How large of a partition would you recommend for UBUNTU? This will be a bare bones install, with most of my apps in Win 7 partition.

Also, is there a way that I can run WinPep7 (DynoJet program) and Engine Analyzer (Performance Trends program) in UBUNTU?

Thank you.

---

### Post by oldfred on 2014-01-20
If not installing much you can get by with as little as 10GB, but may require more maintenance. Often 20GB is a good size as long as you have your data stored in a separate data partition or /home that is separate.

.wine may run some Windows programs, but usually most programs do not run well. And most proprietary programs will not run in Linux. 
Often better to find a Linux application with similar functions. But the less common it is, the less likely you are to find something unless a user has written it and posted it.

---

### Post by brian xpsp2 on 2014-01-20
Hi 
while not strictly relevant to this thread I did a "WUBI" Ubuntu install on a pc with win7 installed,which worked a few times but recently wouldn allow me to boot into win7.After much research (days) I have finally got win7to work again.It appears that this sort of thing can occasionally happen using Wubi.
I now want to uninstall the ubuntu and reinstall directly with so i understand the grub loader in its own partition
Is that correct

---

### Post by oldfred on 2014-01-20
@brian xpsp2
Best not to hijack another thread. If you have questions best to start a new thread with your issues in that thread.
grub2's boot loader is installed to the MBR of the drive or sda if one or first drive, not any partitions. Normal desktops do not need /boot as a separate partition.

---

### Post by Joe_Ciaravino on 2014-01-21
> **oldfred said:**
> On my 64GB SSD I have two Ubuntu installs of 28GB each. I would think it better in your case to make Windows system partition larger and Ubuntu root partition smaller.

Then you can have a larger NTFS shared data partition on the rotating hard drive.

I use two shared data partitions one NTFS and one Linux formatted. I now have stopped using XP but have not yet converted/reconfigured data in NTFS partition into Linux data partition. I link all data back into /home and have used about 11GB of / (root) including my /home on my working install.

oldfred,

I understand that I'll format the shared (data) drive NTFS, as well as the Win7 partition of the SSD. If I format the UBUNTU partition (decided on 30 gb) of the SSD in LINUX, will it be able to access the shared data partition, which is NTFS. OR must I format the UBUNTU drive NTFS as well? I've been told that running UBUNTU in NTFS may decrease efficiency.

---

### Post by oldfred on 2014-01-21
You cannot run Ubuntu in NTFS except with wubi. 
Wubi's last fully supported version is 12.04 as wubi does not work with gpt partitioned drives. And gpt partitioned drives are required with UEFI boot which all new computers use.

Windows will not read Linux formatted partitions, but the Linux NTFS driver works well with read & write of NTFS data. Best not to write directly into Windows system partition and to set it read only or hidden from Ubuntu. Also turn off fast boot  if Windows 8 or always on hibernation in Windows or any hibernation in any version of Windows  as that restores old partition info, so any files written from Linux then disappear in Windows.

 But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

---

### Post by Joe_Ciaravino on 2014-01-21
> **oldfred said:**
> You cannot run Ubuntu in NTFS except with wubi. 
Wubi's last fully supported version is 12.04 as wubi does not work with gpt partitioned drives. And gpt partitioned drives are required with UEFI boot which all new computers use.

Windows will not read Linux formatted partitions, but the Linux NTFS driver works well with read & write of NTFS data. Best not to write directly into Windows system partition and to set it read only or hidden from Ubuntu. Also turn off fast boot  if Windows 8 or always on hibernation in Windows or any hibernation in any version of Windows  as that restores old partition info, so any files written from Linux then disappear in Windows.

 But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)


Totally unfamiliar with UBUNTU, so you're way over my head.

Bottom line is that I won't be using U for anything more than web browsing.........at least at first, until I decide on how well I like it......or not. The advantage is that it is not easily infected (so I have read), so somewhat risky browsing can be done with chrome on the U side. Dunno whether or not there are any antivirus programs for U, or if I even need any?

I have a 250 gb SSD and a 250 gb HDD. From your last post, it seems that there will be no easy way to share the data partition between Win and U. Is that correct?

Maybe I should simply partition the SSD into a 50 gb U partition which will include system and data files; a 70 gb Win 7 partition for system and program files; a 120 gb partition for NTFS data; use the 250 gb HDD as another NTFS data partition for Win 7.

---

### Post by oldfred on 2014-01-21
I have shared the same NTFS partition with my Firefox & Thunderbird profiles and other data for years. Back in 2006 I started sharing with FAT32, but when I converted to 64 bit, I also converted to NTFS for shared data.

It is the Windows system partition that is best not to share.

---

### Post by Joe_Ciaravino on 2014-01-21
> **oldfred said:**
> I have shared the same NTFS partition with my Firefox & Thunderbird profiles and other data for years. Back in 2006 I started sharing with FAT32, but when I converted to 64 bit, I also converted to NTFS for shared data.

_**It is the Windows system partition that is best not to share.**_

Alright, and thanks very much. This is a desktop and I never hibernate it so any trouble associated is moot.

I believe I understand what to do now:

1.  Set the Win 7 SYSTEM (NTFS) drive to "hidden or read only from UBUNTU" to avoid any POSSIBLE data deletion and/or corruption.
2.  Format the U drive to default LINUX .
3.  Format shared drive to NTFS.
4.  Install win 7 first.
5.  Win 7 system drive on SSD set to 70 gb. 
6.  U syst drive on SSD to 30 gb.
7.  Remainder of SSD (about 150 gb) NTFS, shared documents, audio, video, pictures.
8.  Entire 250 gb HDD shared NTFS.

The NTFS read/write driver bundled with UBUNTU 12.04.3 will allow read/write to the NTFS drives. Still not recommended to write to the Win 7 drive.

---

### Post by oldfred on 2014-01-21
You will be able to read/write both NTFS partitions. And only if you add auto mount settings will you not automatically have read/write to Windows system partition.

---

### Post by Joe_Ciaravino on 2014-02-20
I try to install UBUNTU 12.04.3 and get a menu saying "there is no other o.s. installed on this drive, what would you like to do:

1. Install UBUNTU
2. Something else.

There is an "EFI System Partition" in disk manager. What do I do????? Help!!!

---

