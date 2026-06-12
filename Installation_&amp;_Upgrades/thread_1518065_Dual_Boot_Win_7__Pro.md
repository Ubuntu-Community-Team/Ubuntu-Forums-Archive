---
title: "Dual Boot Win 7  Pro"
date: 2010-06-26
forum: Installation &amp; Upgrades
---

### Post by odatkid on 2010-06-26
[B]Hi All,
 I intend to install Ubuntu 10.4 on a partition on my win7 Pro machine. I'm very new to linux and don't know what file system to format the partition with. Anything else I should know before I install? Both are 64bit.
 Any suggestions would be greatly appreciated.

Thanks........Tom[/B]

---

### Post by wilee-nilee on 2010-06-26
> **odatkid said:**
> [B]Hi All,
 I intend to install Ubuntu 10.4 on a partition on my win7 Pro machine. I'm very new to linux and don't know what file system to format the partition with. Anything else I should know before I install? Both are 64bit.
 Any suggestions would be greatly appreciated.

Thanks........Tom[/B]

Do you want to do a wubi install or dual boot, you mention on a partition but it helps to know what you understand, it is the format part that makes me ask this.

---

### Post by darkod on 2010-06-26
If you plan to make a full ubuntu install, you can't create the partition from windows. And you need to have unallocated space on the hdd not belonging to any partition.

Then when you start the ubuntu installer just use the Use Largest Available Free space option which will install it into the unallocated space.

---

### Post by odatkid on 2010-06-26
[B]
 Hi Guys,
 Thank you for your replies. Sorry I wasn't more clear. I want to dual boot with Win 7 Pro. Here is exactly how the Win 7 Pro drive is now partitioned:

  "System Reserve" 100MB Healthy (System) 
 
  (C) 49.90 GB NTFS Healthy (Boot, Page File, CrashDump, Primary Partition) 
 
  (E) 50.00 GB NTFS Healthy (Primary Partition)  (100% Free)

   New Volume (D)  365.76 GB NTFS Healthy (Logical Drive)  (100% Free)

  I was thinking of installing Ubuntu on the "E" partition and dual booting with Win 7 Pro. I wanted to use the "D" partition as storage space for data from both OS's. I ran the install CD and got to the point of formatting the partition but don't know which file system would be the  ideal choice.
 After choosing the correct file system is there anything else a newbie should know to finalize the installation?
 Thank you again for your help and expertise.

Tom[/B]

---

### Post by darkod on 2010-06-26
Because you are obviously tied to how windows is calling partitions, I will use it temporary, but learn the linux way, it's much clearer. :)

If E: and D: are completely empty of data as you say (100% free), in fact the easiest is to open windows Disk Management and delete them, including the extended partition holding D:.

After that you will end up with approx 416GB unallocated space. Leave it as such.

Boot the ubuntu cd and start the installer. In step 4 select Manual Partitioning. It will show a list of your partitions.

Create a new LOGICAL partition with size 15GB, filesystem ext4, mount point /.
Then create again new LOGICAL partition with size approx 33GB, ext4, mount point /home.
Then again logical partition, size 2GB, swap area (there is no mount point for swap).

That's it.

This is only suggestion, you can adjust the partition sizes to your needs. For example, swap of 2GB is enough but if you plan to regularly hibernate you should make it 1.5 x RAM size. In that case make /home smaller, so in total all three partitions make the 50GB you want to dedicate to ubuntu.

Leave the rest of the space as unallocated again, and just finish the install.

Once it's installed and you can boot it, install Gparted with:

sudo apt-get install gparted

and open it from System-Administration. You will have approx 365GB unallocated space at the end. Make one big logical ntfs partition from it, like you planned, and both OSs can use it. In Gparted you have to click the green button to execute the changes you scheduled, not just close it.

Did all of this make any sense? :)

---

### Post by odatkid on 2010-06-26
[B]Hi Darko,
 Thanks again for your response. I think I get what you mean. I deleted the unused partitions as you suggested and am left with 415.76 unallocated space.

You suggested: From the Ubuntu installation CD,
 "Create a new LOGICAL partition with size 15GB, filesystem ext4, mount point /.
Then create again new LOGICAL partition with size approx 33GB, ext4, mount point /home.
Then again logical partition, size 2GB, swap area (there is no mount point for swap)." 

 As I said I'm VERY new to Linux and would have never thought of creating (2) partitions for the install. (I understand the swap area though). The phrases "ext4" and "mount point" and "mount point /home" are somewhat confusing to me. I think "ext4" is my format choice, correct? Not sure about "mount point" and "mount point /home".

 Thank you again for your help.

Tom[/B]

---

### Post by darkod on 2010-06-26
Usually linux installs use two partitions, the main one called root and marked as / (and the mount point is also called /) which holds the system, and swap.
I suggested a third one, with mount point /home, because it allows easier reinstall later. When you get more familiar with ubuntu, you will see the difference. Making a new installation is ideal chance to create the separate /home partition.

Once you start the installer and the manual partitioning tool, where you need to select the mount point will become clear. The ext4 is the filesystem type, like ntfs for windows.

The partitions have to be created as logical because the hdd has limit of only 4 primary partitions, so all of them can't be primary (including 2 already existing for win7). The logical partitions will be grouped into single extended, which counts as one partition.

---

### Post by odatkid on 2010-06-26
[B]Hi Darko,
 Success! I installed Ubuntu and am dual booting with Win7Pro. I installed Gparted with: sudo apt-get install gparted as  you suggested and I entered my password and all seemed to go well and I formatted the remaining 368GB NTFS. I assume I could've also done that in windows. I am online now with Firefox on Unbuntu (I use Firefox exclusively on Windows).
 I'm simply checking out all the programs on Ubuntu and wanted to know if there is anything else I should do now that it's installed. I have read references to "Gnome" desktop environment and not sure what that's all about.
 Anyway I greatly appreciate all your help and I'm thrilled to finally get Ubuntu installed. I used the CD environment a few times over the last couple of years but this is the first hard-drive installation.

 Thanks again and I'm sure I'll be spending a lot of time on the forums.

Cheers.....Tom [/B]):P

---

### Post by oldfred on 2010-06-27
Several years ago I decided I wanted to convert to Ubuntu. So I created the shared now NTFS (then FAT) partition. But when in windows the firefox and thunderbird were not the same. Also spouse wanted all photos available.

I moved my windows firefox and thunderbird profiles to the shared partition and adjusted my profile.ini in each system to find it. I have not yet converted thunderbird to ver3 but went thru several updates to Firefox without any issue. Once I knew how easy it was to copy profiles, I just copy it to my portable when we travel and back when we return. I also installed the most current version of picasa in wine so the same version is in XP & Ubuntu.

[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)

---

