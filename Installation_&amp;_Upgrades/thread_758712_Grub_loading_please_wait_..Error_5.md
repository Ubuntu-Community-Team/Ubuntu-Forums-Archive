---
title: "Grub loading please wait ..Error 5"
date: 2008-04-18
forum: Installation &amp; Upgrades
---

### Post by mvashi on 2008-04-18
my installation is 
hd 1 -- win XP
hd2 -- Ubuntu hardy 

worked fine till last night and this morning i am getting 
Grub loading please wait .. Error 5

Wonder how do i overcome that
Appreciate any help I can get.

---

### Post by dstew on 2008-04-18
From the [Gnu Grub Manual]("http://www.gnu.org/software/grub/manual/grub.html#Stage2-errors"):> Error 5 : Partition table invalid or corrupt
    This error is returned if the sanity checks on the integrity of the partition table fail. This is a bad sign. You may have a damaged partition table. You can try to repair it with any of a number of partition recovery programs. One that is available in Linux is [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk"). You can probably boot a live CD, install TestDisk on the Live CD system using the Synaptic Package Manager (enable the Universe repository), and check out your hd2 partition table. Or, you could maybe use a Windows disk recovery program, but I don't know much about that.

---

### Post by Herman on 2008-04-18
I agree with dstew, and also, before you go to too much work, just check your partition table to make sure at least one of your partitions has the boot flag.
You can check with the 'sudo fdisk -lu' command from the Ubuntu Live CD or with any partition editor. The best one is the Gnome Partition Editor in the Ubuntu Live CD, go 'System'-->'Administration'-->'Partition Editor', and look for a boot flag there somewhere. If you don't see one, right-click on your Windows partition and click  'manage flags', and make sure there's a boot flag in your partition table.
Maybe I'm wrong and sending you on a wild goose chase, but it might be easier to check that first and it's an easy thing to fix.
I can't imagine how your boot flag might have been removed though. 
Ubuntu doesn't require the boot flag, but there should be one boot flag in your partition table to make it valid. Windows does require the boot flag.

Regards, Herman :)

---

### Post by mvashi on 2008-04-18
Thank you 
Your suggestion worked and the boot flag on the on the Ubuntu drive was removed.

---

### Post by Herman on 2008-04-18
Cool, happy ubuntuing.

---

### Post by dstew on 2008-04-18
Nice fix Herman, I learned something today.

---

### Post by mvashi on 2008-04-18
> **mvashi said:**
> Thank you 
Your suggestion worked and the boot flag on the on the Ubuntu drive was removed.

I think the impression I gave is that I removed the boot flag from the Ubuntu drive.
It is actually the reverse.I checked the boot flag and exited.

I am sorry about the wrong impression

---

### Post by jrom727 on 2008-05-22
Hi Herman,

Your suggestion didn't work for me. I have one HD, i'm trying to dual boot. I'm getting the same error. I did what you suggested, there is a boot flag on ntfs but not on ext3. ntfs is installed on sda1 and ext3 on sda2 (extended). I tried putting the boot flag on ext3 but no luck. 

Any other suggestion/s? 

EDIT: I installed testdisk, partition table showing all green. ( not sure really how to check)  lol

> **Herman said:**
> I agree with dstew, and also, before you go to too much work, just check your partition table to make sure at least one of your partitions has the boot flag.
You can check with the 'sudo fdisk -lu' command from the Ubuntu Live CD or with any partition editor. The best one is the Gnome Partition Editor in the Ubuntu Live CD, go 'System'-->'Administration'-->'Partition Editor', and look for a boot flag there somewhere. If you don't see one, right-click on your Windows partition and click  'manage flags', and make sure there's a boot flag in your partition table.
Maybe I'm wrong and sending you on a wild goose chase, but it might be easier to check that first and it's an easy thing to fix.
I can't imagine how your boot flag might have been removed though. 
Ubuntu doesn't require the boot flag, but there should be one boot flag in your partition table to make it valid. Windows does require the boot flag.

Regards, Herman :)

---

### Post by Herman on 2008-05-23
:) Hello jrom727,
What does your partition table look like when viewed with fdisk?
Please post the output from 'sudo fdisk -lu',
```
sudo fdisk -lu
```

---

