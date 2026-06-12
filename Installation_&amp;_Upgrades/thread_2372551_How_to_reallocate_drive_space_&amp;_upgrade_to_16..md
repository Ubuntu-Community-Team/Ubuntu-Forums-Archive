---
title: "How to reallocate drive space &amp; upgrade to 16.04 inside one partition of laptop..."
date: 2017-09-26
forum: Installation &amp; Upgrades
---

### Post by timothybarry on 2017-09-26
On my Lenovo ThinkPad L430, I have two partitions (see attached). The one labeled sda2 has the original W7. I partitioned the one hard drive and have U14.04 on sda5. 

Without disturbing W7, I want to:
[LIST=1]
[*]shrink the W7 partition to 100 GB
[*] add a partition of approximately 300 GB for shared files between W7 & U16.04
[*]replace U14.04 with U16.04 in the remaining 100 GB (can I just use a bootable USB stick with U16.04 on UNetbootin and choose "other" when installing?)
[/LIST]

I am concerned that I will make a mistake with GParted.
The partitions allocating the 500 GB drive in 1. through 3. above can be different, if anyone thinks a different allocation is warranted.

There seem to be some contradictory methods to do this on the Internet. This is my main computer, so I don't want to create more problems - i.e. I want to do it correctly the first time.

I have backed up my U14.04 and am not worried about losing the files in partition sda5.

Any help would be appreciated.

Thanks in advance for your response(s).

---

### Post by ajgreeny on 2017-09-26
There is no indication of what sda3 is, but it may be very important for the running of your Windows 7.  Do you have any idea what is in that partition?

That will potentially be your biggest difficulty as moving Windows partitions can cause boot failure, so I very strongly recommend that you make any changes to size, or move the Win partitions using only Windows' disk management, not gparted or any third party application, though I admit I am unable to make any comments about third party Windows partition managers.

If it is not too dangerous to do these partition changes you will first need to shrink sda2 using Windows disk management, then move sda3 to the left up to the shrunk sda2, again using Windows disk management, if it is an available operation.
You will then need to enlarge the extended sda4 into the now unallocated space, and finally I suggest you make a new ext4 partition in the unallocated space now sitting in sda4, rather than trying to enlarge sda5.

I note that you have no swap partition; is that because you run with a swap-file instead as is now the default in 17.04 and later?  One or the other is recommanded even if you have lots of RAM; we now suggest 2 - 4 GB swap is sensible even if you have a lot of RAM and the system seldom swaps.

---

### Post by timothybarry on 2017-09-26
ajgreeny, thanks for your reply. After posting, I realized that I have W10, not W7 if it makes a difference. When I get back to my laptop, I'll look into the question about sda3. Also, I recall that Lenovo has some recovery portion (that could be what is in sda3). How would I find out what is in that partition if it's not an os seen in grub?

---

### Post by ajgreeny on 2017-09-26
It is so long since I used Windows that I do not know how you can tell what is in that partition, I'm afraid, but you could perhaps be right about the Lenovo Recovery partition.

---

### Post by timothybarry on 2017-09-26
Here is a screenshot from the W10 application that sees the drive (attachment).

---

### Post by oldfred on 2017-09-26
It may be a Lenovo recovery partition or Windows 10 recovery partition. 
Windows 10 now wants to create another partition. With UEFI & gpt extra partitions are not an issue, but with BIOS/MBR you can only have 4 primary and extended partition for logical partitions counts as one of the primary partitions.

       BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx)
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)

I would just make sure you have a good backup of Windows. My Dell wanted both a Dell backup & a Windows backup and they were a lot different in size. And then I did a full Windows backup with Macrium and it was even larger.
       
 [http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)

---

### Post by timothybarry on 2017-09-26
I have decided to do this one step at a time. I've entered W10 and shrunk the W10 partition using the W10 drive manager. Then, I went back to U14.04 and took a screenshot (attached) of the GParted application. I now show an unallocated portion of 86.33 GB. Instead of adding a partition for files accessible from each OS, I've decided to simply add the unallocated portion to the /dev/sda5 (U14.04) partition. There is a small 450.00 MiB portion between the two. How should I incorporate the 86.33 GiB portion into the sda5 portion? Should I do this while booted into U14.04 and use GParted? I'm a bit nervous at this point. Help is appreciated once again.

---

### Post by oldfred on 2017-09-26
Little key icons show partitions are mounted. Any logical partition mounted inside the extended partition mounts the entire extended partition(and in effect all logical partitions).
So you have to use live installer's gparted.

You have to move unallocated inside the extended partition, move logical partition left & then expand right.
Partition in between makes it a bit more difficult as you have to also move it left first.
Do each step separately.
Any interruption totally corrupts all data inside partition, or you must have good backups. 
Make sure cat is not walking on keyboard, nor thunderstorm outside. Otherwise it should work.

---

### Post by efflandt on 2017-09-27
You cannot use gparted to alter partitions on a drive you are running from. So as mentioned you will need to use gparted on an Ubuntu live/install system (or gparted bootable CD) to move that tiny diagnostic partition sda3 up against the shrunken sda2.

Then assuming you backed up whatever you want to keep from 14.04, I would suggest simply deleting sda5 and sda4. Recreate sda4 as an extended partition in full unallocated space, sda5 logical partition as ntfs for whatever you want to share with Win10, then remainder as sda6 with ext4 format for Ubuntu. Then install 16.04 using "Other" when you get to the partitioning part of install and use sda6 as /.

If for some reason you run into a problem accessing the shared sda5 from Windows, you could try reformatting that partition from Windows.

---

### Post by timothybarry on 2017-09-27
efflandt, oldfred, ajgreeny: Thanks for reply to my request. I need to put this upgrade on hold for about 10 days as I have to prepare and direct a conference. However, I will revisit these suggestions and upgrade to U16.04 by mid October. Thanks for your help!

---

