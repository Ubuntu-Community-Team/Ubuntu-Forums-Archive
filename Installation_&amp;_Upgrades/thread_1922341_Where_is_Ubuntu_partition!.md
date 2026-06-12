---
title: "Where is Ubuntu partition?!"
date: 2012-02-08
forum: Installation &amp; Upgrades
---

### Post by rppc on 2012-02-08
So, I installed Ubuntu supposedly on a partition which I had previously created.
 
During the installation process, if I choose the "Install Ubuntu alongside Windows 7" option, it just won't let choose the drive onto which I wish to install Ubuntu. If I click in the arrow to select another hard drive, the box will just go bold and nothing happens.
 
Therefore, I tried the "Something else" menu. However, no matter how hard I tried to select the partition which I had created, when I clicked the install button, it would just give me an error message, claiming that the file system wasn't defined (although it had been previously set as NTFS, which was the file system showed in the table, in the same line as that partition). I managed to choose the "Ext4 journal something" file system and it allowed me to install Ubuntu.
 
However, when I started Windows, I noticed that the partition I had created was gone. I assume it has something to do with the file system...
 
Take a look:
 
[IMG]http://img820.imageshack.us/img820/9939/partitionj.png[/IMG]
 
There should be a partition called "(A): Ubuntu" in there. As you can see, the C: partition is 110 GB large, whereas the hard drive has 160 GB of capacity.
 
So, how can I change the file system of that partition in order to make it recognisable to Windows?
 
Also, how can I change the dual boot dash board (to switch between the operating systems when turning on the computer) instead of that purple GNU one?
 
Regards,
 
**rppc**

---

### Post by deonis on 2012-02-08
Windows cannot see any other partitions except the ones which have Windows file system on it. Ubuntu or Linux, on the other hand, can see everything :) You started to unravel the power of Linux :)

---

### Post by darkod on 2012-02-08
Windows by default can't see linux partitions. So it's normal that it doesn't show in Computer.

Linux doesn't install on ntfs which is why it didn't work until you selected ext4.

Any particular reason you want windows to see the ubuntu partition? For any files that both OSs need to share, you can use one ntfs partition that both can read.

---

### Post by coffeecat on 2012-02-08
@rppc, as the previous posters have said, you won't see any partitions formatted with a Linux filesystem in My Computer, but Windows can see and display the Linux partitions in the Disk Management Utility. However, it can get very confused if the Linux partitions are logical ones. It then reports them as "healthy primary partition", which they are not, but it does get the sizes right.

If you have several Linux logical partitions, Disk Management will actually report more than the 4 allowed primary partitions, which is impossible. The screenshot is one I posted to another thread about a year ago. It was from a temporary test installation of Vista to a 20GB partition with a 10 GB "D: drive", and then four logical Linux partitions. The 1GB is a Linux swap partition and the three to the right of that were ext4 partitions. As you can see they all show up in Disk Management but the logical partitions show up as primaries.

---

### Post by wyliecoyoteuk on 2012-02-08
If you really need to see the Linux partition from windows, go into the disk manager, under administrative tools, you will be able to see the partition.. 
You can use [http://sourceforge.net/projects/ext2read/]("http://sourceforge.net/projects/ext2read/")to access it.
But be careful when changing things on it.
By the way, the new UEFI BIOS allows more than 4 Primary partitions, and win7 also uses "simple volumes" which can confuse thiings
[http://technet.microsoft.com/en-us/magazine/gg309170.aspx]("http://technet.microsoft.com/en-us/magazine/gg309170.aspx")

---

