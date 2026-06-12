---
title: "Chromium has taken over my system!"
date: 2013-04-03
forum: Installation &amp; Upgrades
---

### Post by pimaster on 2013-04-03
Hello, I am a bit of a newbie and so probably did something terrible and disastrous!
I had a pre-installed copy of windows 7 home, then began dual booting with Ubuntu. I re-installed windows 7 then did the same with Ubuntu. Today I read about using chromium on a netbook to speed up browsing times however when I was just using it on a flashdrive it was still pretty slow so I installed it on the hdd. I had left 20GB unused unpartitioned space on it and so I presumed (more like utterly hoped). I can no longer boot up to the Ubuntu boot selection screen. Sorry that this isn't to do with Ubuntu however I didn't know where else to go.
Should I run the Ubuntu system repair disc? I have the iso file and the disc but can I put that onto my flashdrive and boot it up? Do I have to format and start again? If so, how?

Thank you very much, any help or contribution would be greatly appreciated!
Jonny

---

### Post by darkod on 2013-04-03
If you did what I think you did, you overwrote both windows and ubuntu. Chrome OS doesn't install like ubuntu, into unallocated space. It usually installs on the whole disk.

Yes, you should be able to simply reinstall both windows and ubuntu. Whether from cd or usb, up to you. Note that for usb stick you can't simply copy the files only, you need a bootloader on the stick too otherwise it can't boot.

---

### Post by pimaster on 2013-04-03
Okay, I will try that. I know how to burn iso files onto a memory stick. The one thing that made me think that it didn't delete everything is that it only took about a minute to install onto the hdd. Not even enough time do a quick format. Any ideas?

Thanks

---

### Post by darkod on 2013-04-03
Quick format (deleting the partition table) is done in seconds. If you want to, you can try restoring the partitions instead of reinstalling. But any data present on the sectors that were written by Chrome OS is gone. You can use testdisk to restore partitions if you want to.
[http://cgsecurity.org/wiki/TestDisk_Step_By_Step](http://cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by darkod on 2013-04-03
Besides, if you boot into live mode with the ubuntu cd/usb, you can take a look which partitions exist and which don't.

---

### Post by pimaster on 2013-04-03
Okay thanks. Also my memory stick has a 4GB capacity however after formatting from having Chrome OS on it, it now only recognises as 1G?B

---

### Post by darkod on 2013-04-03
Because it made a 1GB partition. Since windows works only with the first partition on a stick and doesn't usually partition it, it will reformat it as 1GB.

Plug it into a linux machine, delete that partition or the whole partition table, make a new table and all will be fine.

---

### Post by pimaster on 2013-04-03
Thank you, okay one last thing... do you know of a good ISO converter so that I can boot from USB? I have downloaded about 5 but I can't seem to get any of them to work. The iso is stored in an os iso file on my windows 8 partition of my desktop which I can access from my Ubuntu partition so should I run the iso converter from Ubuntu. Well I think I can access the files, I can with documents and other files which I have tried.
Thank you very much!
Jonny

---

### Post by darkod on 2013-04-03
If you have a working ubuntu I would recommend the built-in Start Up Disk Creator. And just in case, copy the ISO temporarily in your home folder, don't use it from the windows partition.

When you start the program it will ask you which ISO you want to use, and the destination partition (not disk, partition, if I remember correctly, like /dev/sdb1). And it's better for the partition to be FAT32 so format the stick first as FAT32. Doesn't matter if it's still 1GB, or open Gparted, Create New Partition table, and then create single FAT32 partition. Then use it in the start up disk creator.

It's always best to create it on ubuntu if you have one working.

For windows, try unetbootin or universal usb installer. Note that in windows you will probably need to start the program with right-click, Run As Administrator, to give it max permissions to write the boot sector on the stick. Otherwise it might fail. Also in this case it's best the stick to be formatted as FAT32 before you start.

---

### Post by pimaster on 2013-04-03
Thank you so much Darko, the ubuntu community is amazing! One last quick question, why does ubuntu say that capacity is slighty more. e.g. windows says my memory stick had 1GB, ubuntu 1.1 GB?

Jonny

---

### Post by darkod on 2013-04-03
In windows, 1GB usually means what is knows actually as 1GiB.

The GigaByte should be 1000x1000x1000 bytes, in decimal.
The GibiByte should be 1024x1024x1024 bytes, in binary, the way memory is manufactured and organized.

When linux usually says GB it's the Gigabyte, and GiB is used for the Gibibyte.

However I'm not sure if some linux tools don't use GB for Gibibyte too.

---

