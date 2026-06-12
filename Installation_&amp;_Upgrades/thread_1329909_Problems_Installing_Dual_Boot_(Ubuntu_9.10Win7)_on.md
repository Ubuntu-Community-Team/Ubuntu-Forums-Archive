---
title: "Problems Installing Dual Boot (Ubuntu 9.10/Win7) on HP dm3"
date: 2009-11-17
forum: Installation &amp; Upgrades
---

### Post by DrawnToScale on 2009-11-17
After an easy dual boot install of 8.10 with WinXP, I'm eager to install Ubuntu 9.10 as a dual boot on a new HP dm3 notebook with Win7.  I do not have the Win7 install disk, but rather the recovery disks that come with the computer. These disks (I believe) reformat the hard-drive when used, so - rather than use the Ubuntu partitioner to create a smaller space for a Win7 install - I instead need to install Win7 from the recovery disk and then install Ubuntu.
After using the recovery disks, I&#8217;m left with 4 (primary?) partitions: 

· /dev/sda1  NTFS  200 MB Windows 7 Loader
· /dev/sda2  NTFS  285 GB Windows Vista Loader  (why Vista?)
· /dev/sda3  NTFS  12.6 GB Windows Vista Loader  (Recovery partition)
· /dev/sda4  FAT32 Some mysterious 103 MB partition. 

What are these 200MB & 103 MB partitions after using the Win7 recovery disks? Do I need them both? If I&#8217;m installing Win7, why is &#8220;Vista&#8221; showing up here as the main partition?

I&#8217;ve already used the Ubuntu partitioner to remove the Recovery partition (since I have the recovery CDs) and shrink the main 285 GB NTFS partition down to a 60GB /windows partition. That leaves me with 3 primary partitions. I&#8217;m still able to boot with computer with Win7 and everything seems to be working fine. 

I created a 60 GB /ext4 partition for Ubuntu. I created a 12GB /swap partition (I have 4 GB of RAM) &#8211; yes &#8211; I know that&#8217;s overkill. Now &#8211; I want to create a data partition with the remaining space that can be used by either Ubuntu or Win7, so it needs to be NTFS. When I go to create a new partition using the Ubuntu partitioner,[COLOR="Red"] I am not given the choice of creating an NTFS partition. Why is that?[/COLOR] Have I run out of primary partitions? Can I create a logical NTFS partition? Is there some other way I should go about setting up my partitions? 
Ideally, I&#8217;d like:

· 60 GB NTFS partition for Win7
· 60 GB /ext4 partition for Ubuntu
· ~10 GB swap partition
· ~170 GB (or whatever is left over) NTFS partition for Data 
· Whatever other partitions Win7 insists upon.

How can I achieve this starting with the Win7 recovery?
Thank you for any advice!

---

### Post by darkod on 2009-11-18
The Ubuntu partitioner you are using, is it in live environment (booting and selecting Try Ubuntu option), or in the actual install process when you select Manual Partitioning?

---

### Post by DrawnToScale on 2009-11-18
> **darkod said:**
> The Ubuntu partitioner you are using, is it in live environment (booting and selecting Try Ubuntu option), or in the actual install process when you select Manual Partitioning?

I'm using the Ubuntu install disk, and going through the install process - choosing the manual partitioning install option.

---

### Post by darkod on 2009-11-18
It's strange it's not allowing you to create ntfs but not a problem.
Create your / and swap and leave the rest as blank, unpartitioned space. You will create ntfs partition there from within win7.
Just be careful when creating / and swap, after the third primary partition start creating logical ones.
At the moment you have:
win boot 200MB primary
win7 60GB primary

Create / 60GB primary and then swap 10GB logical. See if Ubuntu will install and run OK, whether the grub2 menu will work and the entry to select win7 working OK. Afterwards you will create the big ntfs data partition either from win7 or ubuntu.

---

### Post by DrawnToScale on 2009-11-18
> **darkod said:**
> It's strange it's not allowing you to create ntfs but not a problem.
Create your / and swap and leave the rest as blank, unpartitioned space. You will create ntfs partition there from within win7.
Just be careful when creating / and swap, after the third primary partition start creating logical ones.
At the moment you have:
win boot 200MB primary
win7 60GB primary

Create / 60GB primary and then swap 10GB logical. See if Ubuntu will install and run OK, whether the grub2 menu will work and the entry to select win7 working OK. Afterwards you will create the big ntfs data partition either from win7 or ubuntu.

At the moment I have:
 NTFS 200 MB Windows 7 Loader (primary)
 FAT32 103 MB Some mysterious partition.  (primary)
 NTFS 60 GB Windows Vista Loader (why Vista?)  (primary)
 ext4  60 GB (for Ubuntu)  (logical partition)
 swap 12 GB (primary?)
 ~170 GB Free space

I don't know what this primary FAT32 103 MB partition is that my Win7 recovery CD created.  It would be great to delete it - but I'll keep it for now.

I may already have 4 primary partitions.  Maybe this is my problem?  Perhaps I should delete my swap partition and make sure its logical, not primary?  Tonight - I'll try creating that large NTFS partition and use the Win7 tools if I can't get the Ubuntu partitioner to do it.

Thanks!

---

### Post by darkod on 2009-11-18
It wouldn't allow you 4 primary + logical ones. I wasn't aware of the 103MB one.

Leave both small ones (200MB and 103MB) primary together with your win7 60GB. Ubuntu doesn't care if it's completely on logical partitions, unlike windows.
So / and swap would be logical, + the big ntfs data you want.
It would be better if the ubuntu partitioner allows you to create the big ntfs also, even if it doesn't at installation hopefully later when you run ubuntu Gparted will allow you.

If somehow swap is primary right now you definitely want to delete it. You can only have 3 primary + 1 extended (with logical ones inside).
It's real shame you don't have win7 dvd, your disk partitions would look much better if you didn't have to use restore dvd.
I read somewhere that if you request a disc media for an originally purchased windows they are obliged to send it to you. I don't know how it works in practice though.

---

### Post by DrawnToScale on 2009-11-18
> **darkod said:**
> It wouldn't allow you 4 primary + logical ones. I wasn't aware of the 103MB one.

Leave both small ones (200MB and 103MB) primary together with your win7 60GB. Ubuntu doesn't care if it's completely on logical partitions, unlike windows.
So / and swap would be logical, + the big ntfs data you want.
It would be better if the ubuntu partitioner allows you to create the big ntfs also, even if it doesn't at installation hopefully later when you run ubuntu Gparted will allow you.

If somehow swap is primary right now you definitely want to delete it. You can only have 3 primary + 1 extended (with logical ones inside).
It's real shame you don't have win7 dvd, your disk partitions would look much better if you didn't have to use restore dvd.
I read somewhere that if you request a disc media for an originally purchased windows they are obliged to send it to you. I don't know how it works in practice though.

How do I go about creating an extended partition and then create logical ones inside?

If I want the large NTFS data directory to be accessable to both Win7 and Ubuntu - can it be a logical partition, or must it be primary?

I'll look into getting a "real" Win7 install disk.

Thank you Darkod!

---

### Post by darkod on 2009-11-18
In windows when you create the partition it's actually called extended. But in ubuntu simply select logical and that's it. The choice will be primary or logical. Extended partition is automatically selected if I'm not wrong when creating logical one.

Yes, both ubuntu and windows will have no problem seeing the data ntfs even if it's logical (extended). If you didn't have the unnecessary two small primary partitions you could make other plans, but it would work like this too.

Maybe during the next clean install of both OSs you will change the partitions.

I'm not too sure, but I think if you have legal certificate (copy) of windows you are allowed to use image downloaded on the internet and use your CD-KEY. Not sure if microsoft offers them directly for download though. You might want to google about that little bit too. The point is to find a version that will work with your cd-key, unless all of them work.

---

### Post by oldfred on 2009-11-18
I do not know what the recovery disk does but a clean install of Win7 creates a small 100mb boot partition. One of your small partitions is that so do not delete it.

If you are using gparted 
starting with Vista - MSoft made some changes to the way it installs itself in a partition. Gparted can deal with it but should have the round to cylinder unchecked.
Herman on checkbox
[http://www.uluga.ubuntuforums.org/showpost.php?p=7816261&postcount=17](http://www.uluga.ubuntuforums.org/showpost.php?p=7816261&postcount=17)

It may be worthwhile to have a repair disk. It is not a full install but will allow repairing win7
If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista or Win7 Recovery Disc 
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

---

### Post by DrawnToScale on 2009-11-21
> **darkod said:**
> In windows when you create the partition it's actually called extended. But in ubuntu simply select logical and that's it. The choice will be primary or logical. Extended partition is automatically selected if I'm not wrong when creating logical one.

Yes, both ubuntu and windows will have no problem seeing the data ntfs even if it's logical (extended). If you didn't have the unnecessary two small primary partitions you could make other plans, but it would work like this too.

Maybe during the next clean install of both OSs you will change the partitions.

I'm not too sure, but I think if you have legal certificate (copy) of windows you are allowed to use image downloaded on the internet and use your CD-KEY. Not sure if microsoft offers them directly for download though. You might want to google about that little bit too. The point is to find a version that will work with your cd-key, unless all of them work.

darkod,
Just wanted to say thank you.  I created my extended NTFS Data partition in Win7 (as you suggested), went back into the Ubuntu partitioner & created my swap and ext4 partitions.  The rest of the dual-boot install went smoothly.  I'm psyched to be able to access a Data partition from either system.  Thanks again!  :D

---

### Post by darkod on 2009-11-21
No problem. Enjoy it now. :)

---

### Post by simeon87 on 2010-02-06
The ~100 MB partition at the end is called HP_TOOLS and it contains tools that HP has installed for your machine. On my HP dm3-1010ed, it only contains a visual interface for system diagnostics (which can be accessed when booting) and that will still work when deleting the partition, it just means you'll have a text interface instead of a visual interface. You can boot into Ubuntu using a live CD or USB stick to browse the contents and to back it up. Each directory in the Hewlett-Packard directory contains a tool; you can search online to see what they do and what functionality you'd lose when deleting that partition (which is what I've done for my dual-boot, see [here](http://ubuntuforums.org/showthread.php?t=1400095)).

---

