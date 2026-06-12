---
title: "Dual boot question"
date: 2010-12-04
forum: Installation &amp; Upgrades
---

### Post by zekegeek on 2010-12-04
I want to dual boot 10.10 and Vista. I already have made a 10 GB partition with EASEUS Partition Master. So how exactly do I install on this partition? I need a good, to the point walkthrough. Thanks. :popcorn: ilikepopcorn

I already have installed the 10.10 ISO on my flash drive thru UNetbootin

---

### Post by Whoop365 on 2010-12-04
sorry this will not be too indepth, hopefully someone else will respond to this.

But I am dual booting.
and here is how i did it.

Had vista installed first, the grub menu( to choose vista or ubuntu at startup works better that way apparently) and i used the usb ubuntu install from ubuntus website. when you go to install with it, it opens a partition managager that you tell where to install ubuntu, just make sure BEFORE you choose an area that it is not your windows partition. Hope this helps slightly.

---

### Post by akand074 on 2010-12-04
You should probably make another partition now equal to the amount of RAM you have to set as a swap partition. Here is how you can do a manual install from here.

1. Plug in your flash drive and turn on your computer. Depending on your BIOS settings it might automatically try to boot into the flash drive or you'll have to go into the boot menu and choose your flash drive.
2. Once the installer finishes booting you can either choose to try it out from your flash drive for a bit first, or install right away. Up to you, when your ready choose to install.
3. You'll now be given an option on whether to install Ubuntu side by side with Windows, Use to whole disk for Ubuntu, or do it manually. Since you already made your partition, I assume you'll want to do it manually. So select that.
4. Now you'll be taken to a partition manager. Find your 10GB Partition and choose to edit it. Set it to format as EXT4, Primary partition, beginning, with mount point "/" without the quotations. The mount point is very important. Set it to format that partition.
5. Find the partition you made equal to the amount of ram you have and set it as "swap". That's it for that one.
6. Make sure NOTHING else but those partitions is checked to "Format" for whatever reason. Click next and confirm the changes.

---

### Post by zekegeek on 2010-12-04
> Find the partition you made equal to the amount of ram you have and set it as "swap".

So you want me to make another partition that's 2 GB (my RAM size) and set that as "swap?"

---

### Post by akand074 on 2010-12-04
> **zekegeek said:**
> So you want me to make another partition that's 2 GB (my RAM size) and set that as "swap?"

I do. You can set it as swap from the Ubuntu installer later. Really you'll just want to make 12GB of free space, then use that 12GB to make your swap and Ubuntu filesystem partition.

---

### Post by zekegeek on 2010-12-05
Alright. So how do you install on that partition after you've set is as  swap and filesystem  Do you just select it under the list of partition with one  click and then hit "Install?"

---

### Post by akand074 on 2010-12-05
> **zekegeek said:**
> Alright. So how do you install on that partition after you've set is as  swap and filesystem  Do you just select it under the list of partition with one  click and then hit "Install?"

No. It will automatically know. The partition you set to have mount point "/" becomes your Ubuntu partition be default. "/" is almost like Window's "C:/". If you want to have a data partition you can make a partition for it and put it's mount point as "/home" (basically the "Users" folder from Windows gets its own partition and Ubuntu connects them seamlessly so you don't even notice that it's on a different partition).

---

### Post by wilee-nilee on 2010-12-05
Personally we don't really know what you have done post this script before following any information please.

So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags  paste all the text in between.

---

### Post by zekegeek on 2010-12-05
> The partition you set to have mount point "/" becomes your Ubuntu partition be default.

But I want to install it on the partition I made which is on /dev/sd5. So how do I select that one? I set it as swap and filesystem, and then what?

---

### Post by wilee-nilee on 2010-12-05
> **zekegeek said:**
> But I want to install it on the partition I made which is on /dev/sd5. So how do I select that one? I set it as swap and filesystem, and then what?

We don't even really know what you have done, what type of partitions built nor the amount you have already. If you want help at a informed level you have to inform us so post the bootscript.

---

### Post by akand074 on 2010-12-05
> **zekegeek said:**
> But I want to install it on the partition I made which is on /dev/sd5. So how do I select that one? I set it as swap and filesystem, and then what?

Like I said, through the Ubuntu installer. Once you get to the manual install, it will open a partition manager. Then you choose the partition you made for the filesystem and swap and do what I said to do for each partition. Click next and it will install Ubuntu on that partition.

---

### Post by zekegeek on 2010-12-05
OK I will run that hold on

---

### Post by zekegeek on 2010-12-07
> **akand074 said:**
> Like I said, through the Ubuntu installer. Once you get to the manual install, it will open a partition manager. Then you choose the partition you made for the filesystem and swap and do what I said to do for each partition. Click next and it will install Ubuntu on that partition.

I shall try that. Thank you.

---

### Post by zekegeek on 2010-12-11
Thank you very much.

---

