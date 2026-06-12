---
title: "Disaster Recovery"
date: 2008-11-15
forum: Installation &amp; Upgrades
---

### Post by mpierce on 2008-11-15
Using Kubuntu Hoary Hairy. Working a very long shift and issued command sudo rm -rf /etc/ when I meant to issue sudo rm -rf etc/

I desperately need urgent help!

How do I recover before computer shutsdown?

---

### Post by aysiu on 2008-11-15
You can't recover *before* the computer shuts down, but if you boot a live CD, you can install *testdisk* and then run *sudo photorec* to try to recover your data.

By the way, Hoary doesn't get security updates any more. You might want to think about upgrading after you've saved your data.

---

### Post by mpierce on 2008-11-15
OK - accept that the version is 8.04
I've reboot the computer with cd disk and I have the main install screen.

How do I boot it so it will go into recovery mode so I can try to restore this?
linux repair installation

---

### Post by mpierce on 2008-11-15
Anyone?

I've got Testdisk operating and reading my disk.
How do I find the data /etc/ ?

I really need help?

---

### Post by inobe on 2008-11-16
if i understand correctly' you wish to recover data, correct ?

if yes, connect a formatted drive to that box and run a live cd, mount both the backup drive and kubuntu drive.

open both drives then drag and drop your data

---

### Post by mpierce on 2008-11-16
I accidently erased the partition /etc

I'm wondering if there is a way I can recover data and files?

---

### Post by inobe on 2008-11-16
i hope i am helping

doesn't root partition contain the exact same directory ?

---

### Post by Herman on 2008-11-16
Here's a link for you to read, [Why Recovering a Deleted *Ext3 File* Is Difficult . . .]("http://www.google.com.au/url?sa=t&source=web&ct=res&cd=1&url=http%3A%2F%2Flinux.sys-con.com%2Fnode%2F117909&ei=lMEfSZDIJonYsAOHlpDPCA&usg=AFQjCNHj893TEwUTUXuDpA1s4akpv-kM3g&sig2=NC_qnfRhxy16Vs0X2XhC3w")

PhotoRec can recover your files but they'll have strange file names. If they were personal files you can open them and identify and rename them and restore them, but operating system files will be a lot of work to identify. I doubt if you'll be able to rename them correctly and restore them. It would at least be a lot of work, like a jigsaw puzzle, only worse.
Your personal files should still be okay at this stage, all you need to do is copy them to some other media if possible.

I think if that happened to me I'd do what inobe advised the first time and use the Live CD and an external USB hard drive to make a backup of my data with, then re-install.
Re-installing would only take about half an hour or a little longer. Backing up and restoring your personal data may take the longer, depending on how much data you have to copy back and forth.

If you don't have a USB external hard drive, or anywhere else to put your data, you might be able to use your Live CD to delete everything out of the partition except your /home/username directory.
Then resize the partition as small as you can and re-install in a new partition beside it and copy the files into your new Ubuntu right after you re-install.
That would be riskier (In case of a partition table disaster), since you would be leaving your backup files on the same hard disk that you are partitioning, but it should work.
TestDisk is an extremely useful program for fixing your partition table if that did happen.

---

### Post by RealG187 on 2008-11-16
> Ideally, the file will be allocated consecutive blocks, but this is not always possible.
That's where fragmentation comes in, right?

Speaking of which, how do EXT drives not get fragmented?

---

### Post by Herman on 2008-11-16
> Speaking of which, how do EXT drives not get fragmented?     They can begin to get fragmented when more than around 80%  of the available space is used up. 
Your Linux partition should be large enough to contain all the files you want and still leave at least 20% spare. If it gets too full, you should probably either delete some files or resize your partition larger.
Here are a couple of links that you might enjoy,  [LEFT][OneAndOneIs2 - Why doesn't Linux need defragmenting?]("http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting")
                        
                        [ITworld.com - Fragmentation and Unix file systems]("http://www.itworld.com/Comp/3380/nls_unixfrag040929/index.html")

Regards, Herman  :)
[/LEFT]

---

