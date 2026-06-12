---
title: "Install 9.10 without grub in mbr"
date: 2010-05-20
forum: Installation &amp; Upgrades
---

### Post by Non-programmer on 2010-05-20
I've installed Ubuntu 9.10 on my netbook before, but I used the Windows installer, I'm now preparing to install straight to the hard drive, I'd like to do so without writing grub to the mbr. 
I have another boot loader I'd like to use to start grub from a partition if possible.
The reason for all this mess is that I run a very small partition with barts pe installed to the drive and I still have to maintain the XP for a while longer.
Thank you in advance for any help you can provide.

---

### Post by bumanie on 2010-05-20
You will have to choose 'manual partitioning' and at about the 6th or 7th step, when it says it is going to install grub to the mbr (or something to that effect), you will need to click on the 'advanced' button and choose the partition to which you want to direct grub, ie the root partition of ubuntu. [Look here]("http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml"), there is a section on manual partitioning and should be of help in guiding you.

---

### Post by Non-programmer on 2010-05-20
I'm wandering, would I be better off to boot the whole thing with grub. 
The configuration will be :
Barts PE (on an ntfs partition)
XP again on an ntfs partition
and Ubuntu
There will be a small (2 or 3 gig) fat32 partition used to move files from XP into Ubuntu. 
Thanks again.

---

### Post by darkod on 2010-05-20
> **bumanie said:**
> You will have to choose 'manual partitioning' and at about the 6th or 7th step, when it says it is going to install grub to the mbr (or something to that effect), you will need to click on the 'advanced' button and choose the partition to which you want to direct grub, ie the root partition of ubuntu

You can use Manual Partitioning for more controls how and what size your partitions are created, but that is not necessary for telling grub2 where to install. Regardless whether you use manual partitioning or one of the guided methods, you will still have the Advanced button in the last screen of the installer.

As for whether it's better to boot everything with grub2, usually grub2 is very good in booting stuff. It depends on your setup. How does the Bart PE work, does it have it's own boot files? As long as it has boot files, grub2 will find them and create a menu entry. Selecting that can start the Bart PE boot process.

Also, for your small partition for sharing files. There is no need for it to be FAT32. Ubuntu is good at reading/writing to NTFS, and XP can use that too. So why not NTFS?

---

### Post by Non-programmer on 2010-06-01
I'm sorry for not checking back my internet was down, I chose to boot all of it through grub and for my purposes it worked out great. I would like about 30 seconds instead of 10 but I think I will survive it.

---

### Post by Non-programmer on 2010-06-01
> **darkod said:**
> Also, for your small partition for sharing files. There is no need for it to be FAT32. Ubuntu is good at reading/writing to NTFS, and XP can use that too. So why not NTFS?

Because I didn't know Linux could now read and write NTFS the last time I had an up and running Linux box it was Slack and (NTFS...noway ).

---

### Post by darkod on 2010-06-01
> **Non-programmer said:**
> I'm sorry for not checking back my internet was down, I chose to boot all of it through grub and for my purposes it worked out great. I would like about 30 seconds instead of 10 but I think I will survive it.

9.10 and 10.04 come with grub2, so if you did clean install of any of the two versions, you probably have grub2.
To adjust the timeout open the file:

sudo gedit /etc/default/grub

just adjust GRUB_TIMEOUT=x. After saving and closing the file, to recreate updated grub.cfg in grub2 you need to run:

sudo update-grub

---

