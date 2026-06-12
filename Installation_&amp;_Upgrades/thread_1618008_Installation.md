---
title: "Installation?"
date: 2010-11-10
forum: Installation &amp; Upgrades
---

### Post by Yezinki on 2010-11-10
Hi there,

Plan installing Ubuntu 10.04 LTS  ONLY, BOTH on my desktop & laptop.

1. How do I proceed........as  to how many, types, sizes, file systems of partitions.......I think would need /boot, /root, /swap, /home (on a separate partition)?

2. Size of HDD are 290 GB & 100 GB respectively.

3. Once partitions are created & Ubuntu installed would like to create a full back up image just in case?

4. If the Linus OS files get corrupted or need a reinstall is it possible to just install it in the /root with out changing/recreating other partition structures?

5. Is Ubuntu version stable enough, any advantage of any other version or 64 bit vs 32 bit, since want to install once & have a peace of mind for some time......no Linux genius just a retired old MD.

6. Suggestions as to what kind of security steps to be taken & what software to use to create a full back up & where to save the backup?

Kindly guide me step wise,

Yours assistance would be highly appreciated,

Best Regards!

---

### Post by sikander3786 on 2010-11-10
Hi.

> 1. How do I proceed........as to how many, types, sizes, file systems of partitions.......I think would need /boot, /root, /swap, /home (on a separate partition)?

/boot is not absolutely necessary. You can just let '/' partition handle all those boot files.

Having /home on a separate partition helps when you need to reinstall as you'll be able to save all your personal files, settings/config that way.

Swap is indeed handy when you run out of free memory and in suspending/hibernating.

> 2. Size of HDD are 290 GB & 100 GB respectively.

You can have the same structure on the both drives,

If you absolutely need a separate /boot, in my opinion, the partition table will look something like,

sda1: /boot, 512MB, ext3 (Optional, size can be adjusted according to your needs)

sda2: /, 30-40GB, ext4 (40GB has always been enough for all my software/activities)

sda3: /home, ext4 ( Size is Remaining hdd space minus Swap unless you need a separate Data partition)

sda5: Swap, (RAM X 2) (Extended/Logical parition)

sda6: Optional Data partition, custom sized.

> 3. Once partitions are created & Ubuntu installed would like to create a full back up image just in case?

I have never needed that as a clean install only takes 20 min :-). You can use clonezilla.

[http://clonezilla.org](http://clonezilla.org)

> 4. If the Linus OS files get corrupted or need a reinstall is it possible to just install it in the /root with out changing/recreating other partition structures?

Yes. From the installer just choose your previous / partiton, same mount point and mark it for format. Don't choose to format your /home.

> 5. Is Ubuntu version stable enough, any advantage of any other version or 64 bit vs 32 bit, since want to install once & have a peace of mind for some time......no Linux genius just a retired old MD.

I never had any issues with 64-bit. Not even that flash player problem reported too often. As you know 32-bit as well supports RAM more than 3GB with PAE-Kernel, it is always your own decision. It would be better to test your hardware from Live CD before choosing to install 32-bit or 64-bit as sometimes it is reported that some hardware is not supported in one version or the other (extremely rare).

---

### Post by Yezinki on 2010-11-10
Thanks a few queries.

1. Do I really need a /boot or can do with out it?

2. Could you care to post a plan of a dual boot off windows XP/7Ult & Ubuntu 10.04 LTS.......simple step wise.....shall be appreciated?

Best Regards!

---

### Post by sikander3786 on 2010-11-10
This one might answer your first query.

[http://askubuntu.com/questions/6490/is-a-boot-partition-necessary-anymore](http://askubuntu.com/questions/6490/is-a-boot-partition-necessary-anymore)


Regarding dual boot, it is always better to install Windows at the first place and then Ubuntu to save you all the hassle related to re-installation of Grub.

This page will help you understand the required setup.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

If there are no recovery partitions, the partition setup will look something like this.

sda1: Windows partition. Primary partition.

sda2; Data partition, Primary, if you care to have one. (Can share data across Ubuntu and Windows. You can also have it at the last place as wel.)

Rest of the setup will be the same, except that some partitions now need to be moved to extended/logical partitions as you are allowed to have only 4 primary partitions.

sda3: /boot, Primary, 512MB, ext3 (Optional, size can be adjusted according to your needs)

sda4: /, 30-40GB, Primary, ext4 (40GB has always been enough for all my software/activities)

sda5: /home, Extended/Logical, ext4 ( Size is Remaining hdd space minus Swap unless you need a separate Data partition)

sda6: Swap, (RAM X 2) Extended/Logical

Note that you also boot Ubuntu from a logical partition. So installing it to a primary partition is not absolutely necessary.

You've always got choices with Linux ;-)

---

### Post by Yezinki on 2010-11-10
Thanks.

1. No /boot.

2. Approx sizes for XP/W7Ult with MS Off '07 updates, SPs, softwares, utilities etc, sda1 NTFS.

3. File system for sda2 would be NTFS, shared by windows & Ubuntu?

4. Why need a sda5 /home.........when you recommended a shared sda2.....care to comment on significance of sda5?

Regards!

---

### Post by sikander3786 on 2010-11-10
> Approx sizes for XP/W7Ult with MS Off '07 updates, SPs, softwares, utilities etc, sda1 NTFS.

For Windows XP, I think 30GB would be my minimum.
For Windows 7, at least 40GB.

If you can afford some more space, add it to my recommended one's.

> File system for sda2 would be NTFS, shared by windows & Ubuntu?

NTFS. Although Windows now supports ext3 and ext4 (to some extent), I consider Linux's NTFS driver far more stable than the ext one for Windows.

> Why need a sda5 /home.........when you recommended a shared sda2.....care to comment on significance of sda5?

You got it wrong. Shared sda2 partition is intended for holding all your personal data, documents, pictures, music, movies etc. While /home stores all your configurations and later, your data, if you prefer to keep it in your /home. But remember, you can't have your /home on an NTFS drive because NTFS doesn't support Linux permissions system. It needs to be an ext drive.

You can look in your current install's /home to see what it actually contains. Press Ctrl + H to view the hidden directories.

---

### Post by Yezinki on 2010-11-10
Thanks.

With all said, how would you divide a 100 GB HDD for W7 & Ubuntu.......that's the laptop.......or do I need to change to a larger drive or forget dual boot on the laptop?

Regards!

---

### Post by sikander3786 on 2010-11-10
100GB HDD is not that small to handle both Ubuntu and Windows 7 unless you need some space for yourself to save your data to.

You need to create a 30-40GB partition for Windows, 30GB for Ubuntu Root, RAM X 2 Swap partition and whatever left, you can create a data partition there. You can also create a /home in that space or simply if you don't need separate /home, add it to your Windows and Ubuntu root partitions.

---

### Post by Yezinki on 2010-11-10
The plan you made for a dual boot of windows & Ubuntu is fine for the desk top's 298 GB HDD.

Could you care to make one custom dual boot plan, for the laptop's 100 GB HDD...simple & in detail?

Thanks.

---

### Post by sikander3786 on 2010-11-10
sda1: Windows 7, NTFS 35GB
sda2: Ubuntu / partition, ext4, 20GB
sda5: /home, ext4, 35GB
sda6: Swap, RAM X 2

I don't exactly know your needs so it might not suit you exactly. You can resize /home according to your needs or create a data partition NTFS if you decide not to create a separate /home.

The partition setup will be the same. You can resize any of the partitions just according to your needs.

---

### Post by Yezinki on 2010-11-10
Which version Clonezilla should I download...[http://clonezilla.org/?](http://clonezilla.org/?)

Thanks.

---

### Post by Yezinki on 2010-11-10
Thanks.

1. Ram on the laptop is 4 GB so swap should be 8 GB?

2. sda5 /home ext4 shall be shared by W7 & Ubuntu?

Regards!

---

### Post by sikander3786 on 2010-11-10
> **Yezinki said:**
> Which version Clonezilla should I download...[http://clonezilla.org/?](http://clonezilla.org/?)

Thanks.
This one. It is based on Ubuntu Maverick, newer kernel, hence supports more hardware.

[http://clonezilla.org/download/sourceforge/alternative/iso-zip-files.php](http://clonezilla.org/download/sourceforge/alternative/iso-zip-files.php)

If you have any problems with the above mentioned, I'd go for the Debian stable version here.

[http://clonezilla.org/download/sourceforge/stable/iso-zip-files.php](http://clonezilla.org/download/sourceforge/stable/iso-zip-files.php)

---

### Post by Yezinki on 2010-11-10
> **sikander3786 said:**
> This one. It is based on Ubuntu Maverick, newer kernel, hence supports more hardware.

[http://clonezilla.org/download/sourceforge/alternative/iso-zip-files.php](http://clonezilla.org/download/sourceforge/alternative/iso-zip-files.php)

If you have any problems with the above mentioned, I'd go for the Debian stable version here.

[http://clonezilla.org/download/sourceforge/stable/iso-zip-files.php](http://clonezilla.org/download/sourceforge/stable/iso-zip-files.php)


Hi am using Ubuntu 10.04 LTS........whats yr call now?

---

### Post by Yezinki on 2010-11-10
Is G Chrome better browser than FF for Ubuntu?

---

### Post by sikander3786 on 2010-11-10
> **Yezinki said:**
> Is G Chrome better browser than FF for Ubuntu?
This will eventually convert into an endless debate.

It would be better that you post that question in the community cafe. Include a Poll and see the results for yourself.

I use both Chrome and Firefox and both do well for me.

---

### Post by Yezinki on 2010-11-10
> **Yezinki said:**
> Hi am using Ubuntu 10.04 LTS........whats yr call now?


What's yr call??

---

### Post by sikander3786 on 2010-11-10
> **Yezinki said:**
> What's yr call??
Install both of them. If you get problem for any specific website. switch to the other one. Having an alternate is always handy.

By the way, I like the Chrome interface. And it works faster for me. Sssshhhh, there are many Firefox lovers around :P

---

### Post by Yezinki on 2010-11-10
Dont f__k e FF lovers my 2 cents...........

---

### Post by Yezinki on 2010-11-10
Hey man I tried video conferencing using skype it was great e a windows user but my audio didn't go through any clues smart genius??

Thanks again.........

---

### Post by sikander3786 on 2010-11-10
> **Yezinki said:**
> Hey man I tried video conferencing using skype it was great e a windows user but my audio didn't go through any clues smart genius??

Thanks again.........
Not many ideas here... :-(

It would be better to start a new thread in the Multimedia & Video sub-forum.

[http://ubuntuforums.org/forumdisplay.php?f=334](http://ubuntuforums.org/forumdisplay.php?f=334)

---

### Post by Yezinki on 2010-11-11
> **sikander3786 said:**
> This one. It is based on Ubuntu Maverick, newer kernel, hence supports more hardware.

[http://clonezilla.org/download/sourceforge/alternative/iso-zip-files.php](http://clonezilla.org/download/sourceforge/alternative/iso-zip-files.php)

If you have any problems with the above mentioned, I'd go for the Debian stable version here.

[http://clonezilla.org/download/sourceforge/stable/iso-zip-files.php](http://clonezilla.org/download/sourceforge/stable/iso-zip-files.php)

They are both the same...size, file names, versions?

---

### Post by Yezinki on 2010-11-11
clonezilla-live-20101106-maverick.iso??

---

### Post by Yezinki on 2010-11-11
> **sikander3786 said:**
> Hi.



/boot is not absolutely necessary. You can just let '/' partition handle all those boot files.

Having /home on a separate partition helps when you need to reinstall as you'll be able to save all your personal files, settings/config that way.

Swap is indeed handy when you run out of free memory and in suspending/hibernating.



You can have the same structure on the both drives,

If you absolutely need a separate /boot, in my opinion, the partition table will look something like,

sda1: /boot, 512MB, ext3 (Optional, size can be adjusted according to your needs)

sda2: /, 30-40GB, ext4 (40GB has always been enough for all my software/activities)

sda3: /home, ext4 ( Size is Remaining hdd space minus Swap unless you need a separate Data partition)

sda5: Swap, (RAM X 2) (Extended/Logical parition)

sda6: Optional Data partition, custom sized.



I have never needed that as a clean install only takes 20 min :-). You can use clonezilla.

[http://clonezilla.org](http://clonezilla.org)



Yes. From the installer just choose your previous / partiton, same mount point and mark it for format. Don't choose to format your /home.



I never had any issues with 64-bit. Not even that flash player problem reported too often. As you know 32-bit as well supports RAM more than 3GB with PAE-Kernel, it is always your own decision. It would be better to test your hardware from Live CD before choosing to install 32-bit or 64-bit as sometimes it is reported that some hardware is not supported in one version or the other (extremely rare).


1. /root sda1 ext4 40 GB should be  Primary correct??

2. /swap sda5 Logical 8 GB > Location at beginning or end??

3. I have sda1 Primary /root 40 GB, sda5 Logical /swap 8 GB, sda6 Logical ext4/home 20 GB, sda7 Logical ext4 22 GB.........is that fine & can I resize using G parted, if needed later after viewing your expert comments.

Regards!

---

### Post by sikander3786 on 2010-11-11
Go to clonezilla.org > Downloads and then click differences under Other Notes column.

---

### Post by sikander3786 on 2010-11-11
> 
1. /root sda1 ext4 40 GB should be Primary correct??

Yes

> 2. /swap sda5 Logical 8 GB > Location at beginning or end??


Beginning.

> 3. I have sda1 Primary /root 40 GB, sda5 Logical /swap 8 GB, sda6 Logical ext4/home 20 GB, sda7 Logical ext4 22 GB.........is that fine & can I resize using G parted

That scheme looks fine to me. You can resize any partitions but it is recommended that you don't try to resize the Ubuntu root partition.

For resizing, see this,

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

---

