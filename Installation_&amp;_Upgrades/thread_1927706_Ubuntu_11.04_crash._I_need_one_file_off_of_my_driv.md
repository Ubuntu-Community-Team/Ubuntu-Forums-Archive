---
title: "Ubuntu 11.04 crash. I need one file off of my drive... Help appreciated!"
date: 2012-02-18
forum: Installation &amp; Upgrades
---

### Post by Ditto110 on 2012-02-18
Hi guys. I was using my computer fine last night, but suddenly it doesn't work this morning. When I turn it on, immediately after the boot screen (the one where it says press f12 for boot menu) I get a black screen with a cursor in the top left corner. It stays here and doesn't do anything. I have googled this for the last couple of hours but nothing I could find helped me. I am working on a big project for school, and all I want to do is recover that .tex file (my last backup from the file is about a week ago and I have done a fair bit of work to it since).

I have it running with a boot cd right now. I figured I would be able to access my drive from here, but it hasn't been so easy. There are 2 drives: File System and 160 GB Hard Disk: MEDIADIRECT. I can't find any of my files in either of them! It appears as though my drive has been wiped clean. Does anyone know if it is possible to still get the file back? Maybe I'm not looking in the right place? I have used the search function in linux and haven't been able to locate it. 

Thanks for any help guys, it's really appreciated.

---

### Post by darkod on 2012-02-18
The search function and looking inside Filesystem will not work, it considers the live cd as filesystem.

So, the 160GB is another disk, not the one you are looking for, right?

Boot live mode again and try in terminal:
sudo fdisk -l (small L)

Post the results. Does it detect the disk you are looking for?

---

### Post by Ditto110 on 2012-02-18
Thanks for the  reply. Here are the results.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ed863

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *       19066       19457     3148708+   c  W95 FAT32 (LBA)
/dev/sda2           19344       19458      914433    5  Extended
/dev/sda5           19344       19458      914432   82  Linux swap / Solaris

---

### Post by ajgreeny on 2012-02-18
There is no partition for ubuntu showing there other than the swap.
```
/dev/sda1   *       19066       19457     3148708+   c  W95 FAT32 (LBA)  [COLOR=Red]Windows? Certainly not 11.04![/COLOR]
/dev/sda2           19344       19458      914433    5  Extended  [COLOR=Red]Extended[/COLOR]
/dev/sda5           19344       19458      914432   82  Linux swap / Solaris  [COLOR=Red]Logical swap[/COLOR]	
```
sda1 looks like a windows partition and sda2 and sda5 are an extended partition with the swap partition sitting in it.

Somehow it looks as if you have turned an ext4 partition into a fat32 partition, sda1.

What does gparted on the live CD/USB have to show?  Let's see a screenshot.

---

### Post by darkod on 2012-02-18
Not only that, the disk looks almost empty. Up to cylinder 19066 there is nothing shown. EDIT: And the extended partition sda2 is inside sda1 which is impossible.

Looks like your partition went missing.

But first, confirm that this disk of 160GB is the one we are talking about? Was the data on it? Or you expect to see another disk too?

Even if the partition is gone there might be chance to recover it with testdisk.

---

### Post by Ditto110 on 2012-02-18
This computer isn't running windows. I installed Ubuntu and used the whole 160 gb drive for it. The 160 GB drive is the drive I expected to see the data in. I'll go see if I can get a screenshot now. Thanks again.

---

### Post by Ditto110 on 2012-02-18
[IMG]http://farm8.staticflickr.com/7059/6898172505_c001dd22d5_b.jpg[/IMG]

---

### Post by darkod on 2012-02-18
Download and run testdisk:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

Do the deep search, not just the quick search, and post the screenshot with the testdisk search results. DO NOT write any new partition table unless you are sure what you're doing.

The warning in that screenshot is clear, you have overlapping partitions, sda2 and sda1. But this is just part of the problem, sda1 should be much bigger and different type.

---

### Post by Ditto110 on 2012-02-18
Alright will do. I won't write any new partition tables since I have *no* idea what I'm doing.

---

### Post by darkod on 2012-02-18
Don't worry, I just wanted to warn you because it's a powerful tool. But you do need a powerful tool to sort this out. It's nothing to be scared about, but you need caution.

As soon as testdisk finishes in the terminal window, just make a screenshot and post it, without making additional actions.

---

### Post by Ditto110 on 2012-02-18
Noob question, but how can I log in as root? I changed the pass, but in order to login as root I have to log out of my current session. Problem is I am using a boot cd so I can't log out.

---

### Post by darkod on 2012-02-18
No, no, don't touch the root password. While running in live mode you simply use sudo in front of any command that needs to be run as root.

No need to worry about the root user or passwords in the live session.

---

### Post by Ditto110 on 2012-02-18
Thanks, but a new problem:

ubuntu@ubuntu:~/Downloads/testdisk-6.13$ ls
AUTHORS             fidentify_static  photorec.8       testdisk.log
ChangeLog           ico               photorec_static  testdisk_static
COPYING             INFO              README           THANKS
documentation.html  l                 readme.txt       VERSION
fidentify.8         NEWS              testdisk.8
ubuntu@ubuntu:~/Downloads/testdisk-6.13$ sudo exec ./testdisk_static
sudo: exec: command not found



Any idea why? It runs without sudo there. Thanks again.

---

### Post by darkod on 2012-02-18
Sometimes I am also confused how to run these things.

Once you are into the testdisk folder, did you try with only:
sudo ./testdisk-static

---

### Post by Ditto110 on 2012-02-18
Hopefully I did it right. The first is before the deeper search and the second after.

[img]http://farm8.staticflickr.com/7208/6898745051_68f0a03740_b.jpg[/img]


[img]http://farm8.staticflickr.com/7176/6898846877_190baee6ef_b.jpg[/img]

---

### Post by darkod on 2012-02-18
You did, but it doesn't look good, at least not to me.

In the second screen, look above the list, it says "partitions that can't be recovered". The selection is on Continue below the list, if you hit Enter to continue does it show any different list?

Also it complains that the disk is not detected correctly. Can you check in BIOS if it sees it correctly?

For exiting testdisk without any changes just look where it says quit (q). The command to write a table is 'w', so just make sure you never hit w.

Maybe someone else knows more if this can be recovered so they will jump in.

Meanwhile see if you get another list shown after you hit Continue.

Also, if you remember from memory your partition sizes, and how many partitions were on the disk, post it so we at least have some clue.

---

### Post by Ditto110 on 2012-02-18
That's what I was afraid of. For the amount of effort, I'm probably better off just starting from my most recent backup. Thanks for your help though, it's appreciated.

---

### Post by darkod on 2012-02-18
If you are ready to give up, it doesn't hurt trying one thing more. Even if it loses your data, you have your most recent backup. Again I say, if you are ready to give up.

Try fixparts, which can fix smaller partition table issues, like overlapping partitions. Sometimes it's all it takes in order the partition table to "fix" itself.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

