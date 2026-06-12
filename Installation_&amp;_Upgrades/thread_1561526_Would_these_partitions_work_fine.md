---
title: "Would these partitions work fine?"
date: 2010-08-26
forum: Installation &amp; Upgrades
---

### Post by jcd29 on 2010-08-26
I'm planning on formatting my computer, which has two HDDs: An 80GB one, and a 320GB secondary one.

I'm planning on using Ubuntu as my primary OS, allocating 40GB to it, and 40GB to a Windows XP partition. (Maybe 50/30, not sure yet how much I need).

But for the secondary drive, I was planning on making a 280GB partition as ext4 for using in Linux, and a 40GB NTFS-3G partition for storing files in Windows, and being able to share them with the Linux partition whenever I want to.

Does this sound good, or is there something else I should do? Thanks!

---

### Post by jcd29 on 2010-08-26
I also considered the following scenario:

Full Ubuntu installation on 80GB HDD (Or just taking 25 GB for installs and leaving the other 55GB as an ext4 partition for data), and formatting the 320GB HDD as ext4 too. 

And installing Virtualbox to run XP (giving it, let's say...70GB).

This would be ideal for me, really. The problem with this scenario is that Adobe Premiere would probably run way too slow for me this way. My computer has 2GB RAM, and I'd be giving the VM 1GB, which is not enough for Premiere and After Effects to run smoothly, I think. That, and I'm guessing there'd be video card issues in the virtualization. And Steam, which in its latest version isn't quite Gold yet for Wine, IIRC.

So I'm thinking the first scenario is still the best for now.

---

### Post by sikander3786 on 2010-08-26
In my opinion the best scenario will be to install Ubuntu on the 80GB hard disk using up the whole disk.

Then installing Windows on something 30 - 40 GB out of 320 GB. The remaining space in the 320 GB as a single NTFS Partition for data storage working both with Ubuntu and Windows as NTFS-3G is a great great driver for NTFS in Linux.

Edit: Myself use NTFS for data storage b/w Ubuntu and Windows and never ever had any problem.

---

### Post by dabl on 2010-08-26
Personally, I'm able to run my needed Windows apps on a Windows VM, so that approach appeals to me (I use VMware Player).  In that case, all partitions on both drives can be ext4.

25GB is as large as I've ever made the partition for the OS -- that allows for all kinds of downloaded ISO images and such.  But I never store my data with the OS -- it's all on other partitions, in directories cleverly named "DOCS", "PIX", "MUSIC", "VIDEOS", etc. etc.  Matter of fact, I just go ahead and label the partitions that way, too.  Then you can symlink the directories in to your user folder and get to your data that way.

Don't forget to make a swap partition -- your system memory size plus 100MB is fine -- that will let you hibernate it if you should want to do so.

---

### Post by sikander3786 on 2010-08-26
> **jcd29 said:**
> 
And installing Virtualbox to run XP (giving it, let's say...70GB).


I would not recommend Virtualbox because it will be too slow with heavy programs.

---

### Post by jcd29 on 2010-08-26
> **sikander3786 said:**
> In my opinion the best scenario will be to install Ubuntu on the 80GB hard disk using up the whole disk.

Then installing Windows on something 30 - 40 GB out of 320 GB. The remaining space in the 320 GB as a single NTFS Partition for data storage working both with Ubuntu and Windows as NTFS-3G is a great great driver for NTFS in Linux.

I think I do want a big data partition as ext4, since it's a little better than NTFS. Apart from Premiere Pro and a few other things, I don't need Windows that much. Only unfortunate part is that with Premiere, the video files take up a lot of space, so I do need a big chunk.

Is Virtualbox really that much slower, though?


> **dabl said:**
> Personally, I'm able to run my needed Windows apps on a Windows VM, so that approach appeals to me (I use VMware Player).  In that case, all partitions on both drives can be ext4.

25GB is as large as I've ever made the partition for the OS -- that allows for all kinds of downloaded ISO images and such.  But I never store my data with the OS -- it's all on other partitions, in directories cleverly named "DOCS", "PIX", "MUSIC", "VIDEOS", etc. etc.  Matter of fact, I just go ahead and label the partitions that way, too.  Then you can symlink the directories in to your user folder and get to your data that way.

Don't forget to make a swap partition -- your system memory size plus 100MB is fine -- that will let you hibernate it if you should want to do so.
That's something I'd like to do, having a small partition (20-25GB) for the OS, and the rest for data. Maybe not a partition for pictures, one for music, etc, but just a big partition for data, and then a big one in the second HDD too.

It's a shame Premiere and After Effects won't really run well virtualized, though. I'd do that otherwise.

---

### Post by oldfred on 2010-08-26
I originally was about 50-50 with XP when I started using Ubuntu. I created a shared (then FAT now NTFS) partition for data I did want to share between the two systems. Primarily firefox & thunderbird profiles so when in either system I have the same links & email.

I then got a new larger drive and wanted to have space for new system partition(s), separate /home and data as I was converting from 32bit to 64bit for Karmic. After moving /home with all the data I then created /data and my /home was then only 1GB. I have since moved /home back into root with Lucid. My system partitions are 20-25GB with about 6GB used.

I have all my data in one large /data partition but since i copied from my old /home it has folders for all the typical /home data folders plus a few I have added. I mount it hidden and link in each folder back to /home so /home looks like a standard install.

Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
oldfred's versions of data linking from above blog, based on more from comments
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

I link all my folders with one command, run in my home by linking every folder in the mount of my /data:
for i in `echo /usr/local/fred/data/*`;do ln -s $i; done

---

### Post by jcd29 on 2010-08-27
I formated my C drive, left the D drive alone for now (until I finished installing).

So I installed XP in a 30GB partition. Then I went to install ubuntu in the remaining free space.

I chose the option to install them side by side, choosing between them at start up, but for some reason (as you can see in the image), instead of being installed in the remaining 48.5 GB of free space in my primary drive, it was installed in my secondary drive. I didn't really get why, so if you guys can explain I'd be grateful.

[[IMG]http://img641.imageshack.us/img641/3778/img00070201008270020.th.jpg[/IMG]](http://img641.imageshack.us/i/img00070201008270020.jpg/)

I then rebooted, deleted the whole secondary drive partition, and chose the option to "use the largest continuous free space", which used the remaining free space in the primary drive, like I wanted.

---

### Post by jcd29 on 2010-08-27
> **oldfred said:**
> I originally was about 50-50 with XP when I started using Ubuntu. I created a shared (then FAT now NTFS) partition for data I did want to share between the two systems. Primarily firefox & thunderbird profiles so when in either system I have the same links & email.

I then got a new larger drive and wanted to have space for new system partition(s), separate /home and data as I was converting from 32bit to 64bit for Karmic. After moving /home with all the data I then created /data and my /home was then only 1GB. I have since moved /home back into root with Lucid. My system partitions are 20-25GB with about 6GB used.

I have all my data in one large /data partition but since i copied from my old /home it has folders for all the typical /home data folders plus a few I have added. **I mount it hidden and link in each folder back to /home so /home looks like a standard install.**

Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
oldfred's versions of data linking from above blog, based on more from comments
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

I link all my folders with one command, run in my home by linking every folder in the mount of my /data:
for i in `echo /usr/local/fred/data/*`;do ln -s $i; done
How do you have your data partition formatted? Ext4?

I don't know if I understood the bolded part. You have the partition hidden, but you link what is in it to the home folder, so that when you enter /home it looks like a normal install, but it's actually links to your hidden partition. Is that correct?

---

### Post by oldfred on 2010-08-27
If you just mount in /media or /home it will usually show twice in the left panel of places, but you only can click on one of them. I really just wanted the standard file structure but have the data else where. Since I have several installs and reinstalls I created a script to mount my data partition. I followed some of the comments in the blog link I posted to mount in /usr/local and create folders for /usr/local/fred/data.

At the time I created my /data I used ext3 and have not redone it but probably would use ext4 now.

Parts of my script:
sudo mkdir /usr/local/fred
sudo mkdir /usr/local/fred/data
I then add to fstab with the script.

I used to do this but found I could fix the minor error in the blog post by Morgan Hall on the one line version.
#ln -s /usr/local/fred/data/Music
#ln -s /usr/local/fred/data/Documents
#ln -s /usr/local/fred/data/Downloads
etc for every folder in /data

---

### Post by jcd29 on 2010-08-27
> **oldfred said:**
> If you just mount in /media or /home it will usually show twice in the left panel of places, but you only can click on one of them. I really just wanted the standard file structure but have the data else where. Since I have several installs and reinstalls I created a script to mount my data partition. I followed some of the comments in the blog link I posted to mount in /usr/local and create folders for /usr/local/fred/data.

At the time I created my /data I used ext3 and have not redone it but probably would use ext4 now.

Parts of my script:
sudo mkdir /usr/local/fred
sudo mkdir /usr/local/fred/data
I then add to fstab with the script.

I used to do this but found I could fix the minor error in the blog post by Morgan Hall on the one line version.
#ln -s /usr/local/fred/data/Music
#ln -s /usr/local/fred/data/Documents
#ln -s /usr/local/fred/data/Downloads
etc for every folder in /data

Man, now I'm confused :lol:

Is this data partition a partition in your primary drive or is it in another drive? Also, where is the partition mounted? I got totally lost when you said it'd show twice in Places.

Since I'm pretty new to all this, could you explain to me what exactly it is you did with your data? At first I thought it was just linked to your home folder, but now I'm not sure if it's something more complex.

---

### Post by oldfred on 2010-08-27
As a data partition it does not matter what drive it is on. I currently have it mounted in sdb1, sdc5 & sdc7 which are all Ubuntu versions - my old 9.10, my current 10.04 and my test of 10.10. That way I have the same data in which ever system I boot.

UUID does not change as it always is the same partition. I have to create the mount point /usr/local/fred/data before adding it to fstab. I have labeled it Data but mount by UUID, I could mount by label.

# Entry for /dev/sdc6 :
UUID=a55e6335-616f-4b10-9923-e963559f2b05  /usr/local/fred/data    ext3         auto,users,rw,relatime               0  2 

I used to directly mount my NTFS shared data partition into /home directly but then it would show a second time in the left panel.
# Entry for /dev/sdc2 :
UUID=44332FD360AA9657                      /home/fred/shared  ntfs-3g      defaults                             0  0  

But where ever you mount it has to be created first and permissions & ownership set. Although fstab controls some of that.

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

---

### Post by jcd29 on 2010-08-27
> **oldfred said:**
> As a data partition it does not matter what drive it is on. I currently have it mounted in sdb1, sdc5 & sdc7 which are all Ubuntu versions - my old 9.10, my current 10.04 and my test of 10.10. That way I have the same data in which ever system I boot.

UUID does not change as it always is the same partition. I have to create the mount point /usr/local/fred/data before adding it to fstab. I have labeled it Data but mount by UUID, I could mount by label.

# Entry for /dev/sdc6 :
UUID=a55e6335-616f-4b10-9923-e963559f2b05  /usr/local/fred/data    ext3         auto,users,rw,relatime               0  2 

I used to directly mount my NTFS shared data partition into /home directly but then it would show a second time in the left panel.
# Entry for /dev/sdc2 :
UUID=44332FD360AA9657                      /home/fred/shared  ntfs-3g      defaults                             0  0  

But where ever you mount it has to be created first and permissions & ownership set. Although fstab controls some of that.

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
Thanks, I'll re-read those links to see if I understand something this time, because it's hard to wrap my head around all of this. I barely understand it right now. Still very much a Linux newbie :)

Like I said, something I'd like to do is be able to link a folder from one of my partitions to the home folder. Maybe not mount it there, but have the folder linked there so it's easily accesible.

---

