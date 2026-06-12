---
title: "Dual Boot Installation,  help"
date: 2019-10-28
forum: Installation &amp; Upgrades
---

### Post by mikelodeon72 on 2019-10-28
Hi  guys,
I have an HP Pavilion dv7 AMD 64 quad core and 8MB RAM
Running Win7 Home edition
I want to install Ubuntu 18.04 in a 120 GB partition (NTFS) I have  available and I made with win 7

I am starting with CD, connect to internet and installing until I get the HD disk options.
I use the "something else"option  in order to chose the 120 GB I have.
remember I  want Dual Boot
I can't install, I chose the volume and I try to format to ext4 or something  like that but ubuntu can not install there because need a root.
Really I don't have any experience installing ubuntu so I am doing my best here.
Tried WUBI in  windows 7 but no way,  error 404 and can't event start.

any guidance please

Thank you

---

### Post by ubfan1 on 2019-10-28
You have a legacy install, on a DOS partitioned disk, with a limit of four primary partitions.  Windows may have already used all four.  What you need to do is backup everything in case things go wrong, delete one partition (one of the small ones Windows seems to like to have around), and create an extended partition (considered a primary_) in all of the free space.  Then you can create logical partitions within the extended. Make one for the deleted Windows partition and restore it from backup.  The Ubuntu installer should offer to make partitions now, or you can use the "something" else, and  make a root, and any others you wish (swap, home, ... all optional).  You add a partition, size it, select a fs like ext4, and a use (as root). Formatting may be done by checking a box on the new partition.

---

### Post by oldfred on 2019-10-28
If you start creating partitions in Windows it may not use the standard primary, extended & logical partitions, but convert to dynamic partitions.
Are your partitions shown as basic or dynamic in Windows?

Post this from live installer:
sudo parted -l
sudo fdisk -lu

If it shows as SFS that is dynamic from Linux view.

---

### Post by mikelodeon72 on 2019-10-29
I deleted one win partition,  now windows have only 3.
Ubuntu recognize the free space and I was able to create a root partition, ext4. It looked like was OK but once I click the "install " I get the message like "partition creation has failed" and can't move on...
.

What to do

---

### Post by ubfan1 on 2019-10-29
Did you confirm that Windows is not using "Dynamic" parttiions?  ("Basic" is what the type of standard partitions.  Did you create an extended partition, and make root a logical partition within that?  I thought 18.04 used a swap file, so wouldn't need a swap partition, and a single root would be all that the default would create.  Did you use the "something else", and create your root that way?  Did you hashcheck the downloaded ISO and run a media check on the install media?

---

### Post by mikelodeon72 on 2019-10-30
I will do that.
But before... do you think I will miss windows if I install Ubuntu as the only one OS in my notebook?
I would use the regular word processor,  acrobat reader, and some windows programs... 

Thanks

---

### Post by CatKiller on 2019-10-30
> **mikelodeon72 said:**
> I will do that.
But before... do you think I will miss windows if I install Ubuntu as the only one OS in my notebook?
I would use the regular word processor,  acrobat reader, and **some windows programs**... 

Well, that's the kicker, isn't it? None of us can tell you how those programs fit into your computer use.

FWIW, I haven't missed Windows in the past nearly-15 years since I last used it.

Don't be tempted to try to install Acrobat Reader under Ubuntu. Adobe abandoned their Linux version years ago, and the default PDF reader was better in any case. LibreOffice is installed by default, too.

---

