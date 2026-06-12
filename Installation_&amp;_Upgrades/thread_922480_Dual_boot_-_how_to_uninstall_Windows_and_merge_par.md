---
title: "Dual boot - how to uninstall Windows and merge partitions?"
date: 2008-09-17
forum: Installation &amp; Upgrades
---

### Post by ee19921 on 2008-09-17
I have a dual boot DELL inspiron 6000(2.5 years old) laptop with Win Xp and kubuntu. I had partitioned my HD into /, /home, swap and 3 more drives for windows. Now I want to get merge these multiple partitions and have just 1 or 2. Some of these partitions are not contiguous. And I also want to uninstall windows. 

After doing all this, is there anyway to retain all installations and configurations I have done so far in ubuntu? The idea is not to do the OS and other s/w installations all over again.

Edit:

I have an external HD, will it work if I restore just the root partition?


Edit2:

The partitions can't get any messier than this. I did this(I don't know why!) when I installed Fedora. Recently, I overwrote that with Kubuntu. Now, I just want to get rid of Windows and run it on virtually if I ever need it. Please help!

/dev/sda1 fat16 55MB
sda2 fat32 20GB C:\
sda3(extended)
-sda5 fat32 15GB E:\
-sda6 ext3 4GB /
-sda7 fat32 15.48GB F:\
-sda8 swap 1GB
-sda9 ext3 353 MB
-free hidden 8MB

---

### Post by ee19921 on 2008-09-18
soft bump :lolflag:!


Did I post this in the right sub forum?

---

### Post by SkonesMickLoud on 2008-09-18
There's no such thing as "uninstalling" Windoze, but you can delete it.

If you want to move some of your partitions around to clean things up, you'll have to boot to a LiveCD that has a partitioner that allows you to resize/move.  The Ubuntu LiveCD has GParted which will work perfectly.  Moving partitions will take some time, and may break your system.  You'll want to make backup's first.

If you just want to delete Windoze partitions, just install GParted inside of Ubuntu:

```
sudo aptitude install gparted
```

Go to System >> Admin >> Partition Editor

Right click on the partition/s you want to delete, click "Unmount" if it's available, click "Delete" or "Format As..." and choose an FS type.

Do with them as you please.

If you booted to LiveCD and want to move partitions around, do the same, but don't format new partitions.  Right click on the partition/s you want to move and click on "Resize/Move".  It's as simple as drag-and-drop from there on.  Click "Apply" and put go watch a movie.

---

### Post by Herman on 2008-09-18
:-k Hmmm, so you want to tidy up that partitioning arrangement eh?
I'm a little confused here, you said you have a separate /home for Ubuntu, I can see your 4 GB / partition and your swap area and a 353 MB partition there, but that's way too smal to be useful for much, surely that's not your separate /home? I'll just ignore that for now.

If it was me I would use the external hard disk to back up all the data to first. I would make a back up of all the data in the whole hard drive.

Then I would delete the first two FAT32 partitions, 
/dev/sda1 fat16 55MB
 sda2 fat32 20GB C:\ 

Then I would use Gnome Partition Editor or GParted Live CD to copy -sda6 ext3 4GB / , and paste it to the new area of free space you just made at the beginnig of your hard disk.
Gnome Partition Editor or GParted preserves the file system UUID numbers by carrying them forward to the new partition and giving the new UUID number to the old file system, so you won't need to worry about editing /etc/fstab.
You're using Kubuntu though aren't you? I'm not sure if your Kubuntu has Gnome Partition Editor or QTParted, which is the KDE equivalent. QTParted may have changed a lot since the last time I used it. I'm not sure what it would be like if you use QTParted. Probably it's as good as Gnome Partition Editor now.

I would resize it to fill the free space.
It should be given the partition number of 1, that will confuse GRUB, so it won't be bootable at first. 
You can fix it by using your Hardy Heron Live CD to  [Rescue your Linux system with a Live CD]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD")  and edit your /boot/grub/menu.lst in your hard disk, that link tells you how.
Another way you could do that is, you could boot if with [Super Grub Disk]("http://www.supergrubdisk.org/"), instead, and  then edit the /boot/grub/menu.lst with the partition number of (hd0,0) for Kubuntu, to make it bootable from now on. You may need to re-install GRUB to MBR too, but I'm not certain.

Once you have the new copy of Kubuntu booting and running okay in partition number 1, you can delete partition 6 containing the old copy of Kubuntu.
I'd also delete partition numbers 5 and 7.
Then I'd resize partition 1 to fill the free space all the way to the swap area.

That would leave you with a couple of extra partitions after the swap area, I'm not sure what those are for, but those would be easy to delete too if you want, and just move the swap area to the rignt, then resize partition 1 again to take up the free space.

---

### Post by ee19921 on 2008-09-18
Someone suggested me to gave /home in a separate partition outside "/" for some reason(sounded good then). I was only experimenting Fedora then so thought 350 MB would be enough. I have been using the windows partions for storing my data.

I have taken the complete image of my laptop HD in my external HD. So backup is not a problem.

Thanks a lot for the replies! I will try gparted thingy this weekend.

---

### Post by Herman on 2008-09-18
> Someone suggested me to gave /home in a separate partition outside "/" for some reason(sounded good then). I was only experimenting Fedora then so thought 350 MB would be enough. I have been using the windows partions for storing my data.:) Oh, okay then. Now I understand.
If that's the case then maybe make your / around 5 to 8 GB or so, and let your /home fill up the rest of the free space. 

It's okay if you have a separate /home. I don't use a separate /home partition myself, but a lot of other people seem to think it's a good idea. As long as it doesn't make you lazy about making backups of your data to some other media, it's fine.

---

