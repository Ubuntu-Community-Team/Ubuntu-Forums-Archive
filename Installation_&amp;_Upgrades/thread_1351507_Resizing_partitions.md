---
title: "Resizing partitions"
date: 2009-12-10
forum: Installation &amp; Upgrades
---

### Post by sks24 on 2009-12-10
Trying to install 9.10, and I'm at a point at which I'm not sure where to go next.  

On this particular installation, the 9.10 interface doesn't have the "slider" interface to resize partitions like 8.10 did (more on that later), and so I'm hung up on step 5, the "prepare partitions" step.  

Right now there are just two partitions: the 74 GB Windows ntfs partition, and a 5.3 GB Fat32 partition, which I presume is a restore partition.

I want to create an 8GB partition for Ubuntu out of that 74 GB Windows partition, so I selected it, then clicked "Change."  (Is 8GB too small?  What's the smallest partition that will "work.")  

The "Edit a partition" box popped up.  I read that 9.10 uses the Ext4 file system, but that's all I know.  What sort of partitions do I need, using which mount points, and how do I make them?  Do I need a swap partition?  (I don't think there's one on my other laptop.)  

I did see a 9.10 install on youtube that did have the slider.

So I tried to use GParted to create an 8GB partition.  It showed the Windows partition as 69.5 GB.  When I clicked on it to resize it, I couldn't enter new values for the "free space before" or "following" or "new size" boxes.  The slider wasn't enabled, and it said that the minimum and maximum size for new partition was the same value: 71171 MiB.  There was a yellow triangle with an exclamation point in it next to the ntfs partition.     

I first tried to install UbuntuStudio, and it, too, said that the minimum and maximum sizes for the resized partition had to be the same value.  I think it said 71GB, too.

Thanks in advance for all your help.

Scott

---

### Post by Mark Phelps on 2009-12-10
If you have Vista, which I suspect you do, do NOT use the Ubuntu installer to shrink your Vista OS partition; instead, use the Vista Disk Management utility to do that.  You might have to defrag the Vista OS partition a couple of times to get it to allow you to shrink it.  Using the Ubuntu installer runs the risk of corrupting the Vista OS partition and rendering it unbootable.

---

### Post by darkod on 2009-12-10
> **Mark Phelps said:**
> If you have Vista, which I suspect you do, do NOT use the Ubuntu installer to shrink your Vista OS partition; instead, use the Vista Disk Management utility to do that.  You might have to defrag the Vista OS partition a couple of times to get it to allow you to shrink it.  Using the Ubuntu installer runs the risk of corrupting the Vista OS partition and rendering it unbootable.

Actually vista shouldn't mind being shrinked by Gparted, I have done it and it works fine. In fact, with vista you might have to do that because often it puts system data at backof the partition and defragmenting doesn't help.
But the other point is very valid. Do NOT do it with the installer, in one step shrinking vista and continuing to install ubuntu. Gparted is NOT the installer. Use Gparted first, shrink vista partition, boot vista few times to do the disk checks, and only then start the install process.
Of course, using the vista disk management to shrink it is also good idea, if it allows you to do what you want. In my case it was offering only 2GB to shrink and I needed 15GB. Gparted did the job great.

---

### Post by sks24 on 2009-12-10
Oops.  XP home.  I thought of defragging.  Then I unthought of it.  Need to do it anyway.  So I'll start defraggler and let that it run.  It's a 74.6GB drive, 46.7 used, 24.9 free space.  

Thank you Mark.

---

### Post by SuperSonic4 on 2009-12-10
You'll want more than 8gb for ubuntu. I would suggest 20gb minimum (and that's if data such as music and pics is stored on a different partition)

---

### Post by darkod on 2009-12-10
> **SuperSonic4 said:**
> You'll want more than 8gb for ubuntu. I would suggest 20gb minimum (and that's if data such as music and pics is stored on a different partition)

Me too. 15GB as bare minimum if you can't afford to dedicate more. 20GB is better. And as mentioned, that's with no music/videos/large files get saved on ubuntu partition.

---

### Post by sks24 on 2009-12-10
Thanks Darkod:
I'll defrag, and then we'll see what we have.  
Scott

---

### Post by sks24 on 2009-12-10
Thanks Supersonic:

If I go with 20GB, that only leaves me just over 3GB in my Windows partition!  So, 15 GB with fingers crossed?

Scott

---

### Post by SuperSonic4 on 2009-12-10
> **sks24 said:**
> Thanks Supersonic:

If I go with 20GB, that only leaves me just over 3GB in my Windows partition!  So, 15 GB with fingers crossed?

Scott

Should be fine. Many people can install ubuntu in 8 but it does require a fair amount of maintenance

---

### Post by oldfred on 2009-12-10
Gparted is fine except for Vista there is the checkbox, since Vista does not start at sector 63.

starting with Vista - MSoft made some changes to the way it installs itself in a partition. Gparted can deal with it but should have the round to cylinder unchecked.
Herman on checkbox
[http://www.uluga.ubuntuforums.org/showpost.php?p=7816261&postcount=17](http://www.uluga.ubuntuforums.org/showpost.php?p=7816261&postcount=17)

Windows supposedly need about 20% empty space to work ok. I would in between defrags try to houseclean out as much as possible. You will also need a 2GB swap partition.

---

### Post by sks24 on 2009-12-10
Thanks oldfred, and thanks to you all,

I think I'm going to backup, reformat, then install 9.10 Studio, and then image the entire drive.  Problem is, I don't have the recovery cd.  So I'm going to do some research on that problem, and, once solved, I'm going to assume the installation will go more smoothly.  So I'm going to mark this solved.

Again, thank you all very much.
Scott

---

