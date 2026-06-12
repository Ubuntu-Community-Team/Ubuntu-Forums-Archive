---
title: "What's the deal with ext4?"
date: 2009-02-05
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by theozzlives on 2009-02-05
Right now I'm upgrading my test box with the alt CD. Should I be reformatting it instead? Is ext4 all that great that it'll WOW me?

---

### Post by Slug71 on 2009-02-05
> **theozzlives said:**
> Right now I'm upgrading my test box with the alt CD. Should I be reformatting it instead? Is ext4 all that great that it'll WOW me?

Well it will depend on what you do with your test box.
Ext4 boots quicker for some than Ext3 does.
Since Jaunty is still in a dev cycle, Ext4 should really be used so it can be tested.

---

### Post by theozzlives on 2009-02-05
> **Slug71 said:**
> Well it will depend on what you do with your test box.
Ext4 boots quicker for some than Ext3 does.
Since Jaunty is still in a dev cycle, Ext4 should really be used so it can be tested.

I just have my printer/scanner hooked to it Jaunty detects the scanner where I could never get intrepid to find. I leave it on so boot time isn't an issue.

---

### Post by Slug71 on 2009-02-05
In that case you probably wont see any difference with Ext4 over Ext3.
Still recommended to use it though so it can be tested on as wide variety Hardware as possible before release and for future releases.
Seems rock solid though.

---

### Post by theozzlives on 2009-02-05
> **Slug71 said:**
> In that case you probably wont see any difference with Ext4 over Ext3.
Still recommended to use it though so it can be tested on as wide variety Hardware as possible before release and for future releases.
Seems rock solid though.

I know this is treading on forbidden waters, but in Windows XP you can convert FAT32 to NTFS. Is there gonna be such a converter in Jaunty?

---

### Post by Slug71 on 2009-02-05
You can convert Ext3 to Ext4. There are how-to's around here in the forum.
Have a look through some of the other Ext4 threads around here.


Update: Found it.

[http://ext4.wiki.kernel.org/index.php/Ext4_Howto](http://ext4.wiki.kernel.org/index.php/Ext4_Howto)

I think you can do it with Gparted now too. Not sure though.

---

### Post by Kow on 2009-02-06
I'm using a beefed up intrepid install with ext4, no problems as of yet. (Started with 2.6.28 kernel, now 2.6.28.3).

---

### Post by Kevbert on 2009-02-06
There has been a [[COLOR="Red"]bug[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/317781") raised over lost data when using ext4.

---

### Post by theozzlives on 2009-02-06
Thanks about the conversion, I'm just gonna run it on my test box for now in case of data loss. I just recovered from a disaster on my laptop, I hate that.

---

### Post by inportb on 2009-02-06
> **theozzlives said:**
> I know this is treading on forbidden waters, but in Windows XP you can convert FAT32 to NTFS. Is there gonna be such a converter in Jaunty?

You don't even *need* to convert... Ext2/3/4 are forwards and backwards compatible ;)
(tell that to Microsoft)

---

### Post by theozzlives on 2009-02-06
> **inportb said:**
> You don't even *need* to convert... Ext2/3/4 are forwards and backwards compatible ;)
(tell that to Microsoft)

I'm just doing ext4 on my test box to see what the difference is.

---

### Post by TheUnderTaker on 2009-02-10
> **inportb said:**
> You don't even *need* to convert... Ext2/3/4 are forwards and backwards compatible ;)
(tell that to Microsoft)

Actually NTFS is backwards and fowards compatible with different Windows versions.

---

### Post by inportb on 2009-02-10
> **TheUnderTaker said:**
> Actually NTFS is backwards and fowards compatible with different Windows versions.

So is any other filesystem compatible with itself.

---

### Post by steveneddy on 2009-02-10
> **inportb said:**
> So is any other filesystem compatible with itself.

I believe all file systems are compatible with themselves.

---

### Post by Archmage on 2009-02-10
> **inportb said:**
> You don't even *need* to convert... Ext2/3/4 are forwards and backwards compatible ;)

Acctually, after you use the extensions in ext4 they can't be read in ext2 or ext3.

---

### Post by steeleyuk on 2009-02-10
But you can still access the file system, right?

---

### Post by jrusso2 on 2009-02-10
> **TheUnderTaker said:**
> Actually NTFS is backwards and fowards compatible with different Windows versions.

Have you tried using NTFS with Windows 9x its not compatible at all.
or FAT 32 with NT 4.

---

### Post by Gina on 2009-02-10
> **steeleyuk said:**
> But you can still access the file system, right?Wrong!

---

### Post by steeleyuk on 2009-02-10
I see, you enable the extensions and you lose the ability to mount as ext3. I was under the impression that it still allowed access to the file system, except it doesn't use the extents. Good to know...

---

### Post by MacUntu on 2009-02-10
If you mount the filesystem as EXT4 with the "-o noextents" option then you will be able to mount it as EXT3 again.

You also can convert EXT4 back to EXT3 (more work, but still possible).

---

### Post by japju on 2009-02-10
> **Kow said:**
> I'm using a beefed up intrepid install with ext4, no problems as of yet. (Started with 2.6.28 kernel, now 2.6.28.3).

Hi,

Did you actually create a beefed up install CD? If so, do you mind giving a short description how you did it? I'd like to do intrepid install with a latest kernel instead of the packaged one....

---

### Post by talkingwires on 2009-02-10
> **Slug71 said:**
> You can convert Ext3 to Ext4. There are how-to's around here in the forum.
Have a look through some of the other Ext4 threads around here.


Update: Found it.

[http://ext4.wiki.kernel.org/index.php/Ext4_Howto](http://ext4.wiki.kernel.org/index.php/Ext4_Howto)> Unfortunately, Ubuntu chose to make this reason for some unknown reason.Well, that was certainly a well-researched article. Clearly, lots of time was spent putting it together, and I'd certainly trust the author with my filesystem!

---

### Post by theozzlives on 2009-02-10
All this jibber jabber on my thread, and no one has yet to tell me whats so great about ext4..... hmmmmmm......

---

### Post by whoop on 2009-02-10
Just converted my file system to ext4. Everything seems to work :-)
I've heard that converting ext3 to ext4 will not be beneficial for any of the existing files on your converted partition (only for new files created after the conversion). This makes sense. 
So could it be possible to make the old files "true" ext4 by defragmenting the partition completely? Or maybe some process that rewrites every file back to the hard-disk (probably with a live-cd).

Is this possible? If yes how? Maybe with e4defrag (when it is available)?

I find it rather scary that the latest jaunty build can install and even convert a file system to ext4 but that there are no applications to view/modify/defrag it. Even gparted says "unkown format". Scary stuff, sure it will all be working when it reaches beta...

---

### Post by whoop on 2009-02-10
> **theozzlives said:**
> All this jibber jabber on my thread, and no one has yet to tell me whats so great about ext4..... hmmmmmm......

[http://hehe2.net/linux-general/ext4-filesystem-explained-in-plain-english/](http://hehe2.net/linux-general/ext4-filesystem-explained-in-plain-english/)
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_ext4&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_ext4&num=1)

---

### Post by theozzlives on 2009-02-10
> **whoop said:**
> [http://hehe2.net/linux-general/ext4-filesystem-explained-in-plain-english/](http://hehe2.net/linux-general/ext4-filesystem-explained-in-plain-english/)
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_ext4&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_ext4&num=1)

So it's faster with less fragmentation. Is that it? How do you convert ext3 to ext4, is there a tool or command?

---

### Post by Nullack on 2009-02-11
IMHO data conversion is risky, Id leave important data at EXT3 or better still create a new EXT4 storage area and copy it over that way leaving the old data.

Im running EXT4 on / and /home - its good. I did notice some EXT4 changes in the .29 kernel though.

---

### Post by todak on 2009-02-11
> **theozzlives said:**
> All this jibber jabber on my thread, and no one has yet to tell me whats so great about ext4..... hmmmmmm......

Here: [http://en.wikipedia.org/wiki/Ext4](http://en.wikipedia.org/wiki/Ext4) is some information on ext4 that might help answer your questions. :)

---

### Post by Archmage on 2009-02-11
> **whoop said:**
> I find it rather scary that the latest jaunty build can install and even convert a file system to ext4 but that there are no applications to view/modify/defrag it. Even gparted says "unkown format". Scary stuff, sure it will all be working when it reaches beta...

I think the online-defragmantion may be in the next kernel, but this won't be in Jaunty.

---

### Post by theozzlives on 2009-02-11
> **todak said:**
> Here: [http://en.wikipedia.org/wiki/Ext4](http://en.wikipedia.org/wiki/Ext4) is some information on ext4 that might help answer your questions. :)

Well I guess I need a seperate /boot partition to convert... I'll wait for Jaunty final to do my Intrepid, and Hardy machines.

---

### Post by Archmage on 2009-02-11
> **theozzlives said:**
> Well I guess I need a seperate /boot partition to convert... I'll wait for Jaunty final to do my Intrepid, and Hardy machines.

Kindly note that since Alpha 3 there is no need for a seperate /boot-partition. The version of Grub can load directly from ext4.

---

### Post by whoop on 2009-02-11
> **theozzlives said:**
> How do you convert ext3 to ext4, is there a tool or command?

How to convert the file system to ext4 (in jaunty)!
Here's what I did:

Booted jaunty livecd on a system running jaunty and ext3 (on /dev/sda1), opened a terminal:
```

sudo bash
tune2fs -O extents,uninit_bg,dir_index /dev/sda1
e2fsck -pf /dev/sda1
mount -t ext4 /dev/sda1 /mnt
nano /mnt/etc/fstab

```

In fstab I changed "ext3" to "ext4" for the partition I converted (and saved the changes)

---

### Post by whoop on 2009-02-11
> **theozzlives said:**
> So it's faster with less fragmentation. Is that it?

Some people claim that you wont notice that much of a difference in everyday use (maybe for booting). I will definitely be using it in jaunty stable and if there is a good defragmentation method available I won't even do a clean install (I do that as less as possible). Hell, maybe I won't do a clean install anyway. Think of this: when you will update an old(er) program with update-manager you will not only update the program itself you will also make it faster as it's files will be overwritten and the new files will make use of the true ext4 technology. LOL, that's really cool. 
I hope there is/will be some method to view the state of your converted ext4 filesystem so you can see what files are still running in ext3 mode and which in ext4.

ext4 is not only faster there are a lot of improvements:
Larger file system
Persistent pre-allocation
Delayed allocation
32,000+ subdirectories
Journal checksumming
Online defragmentation
Faster file system checking
Multiblock allocator
Improved timestamps

So to summarize you could say: newer, faster, bigger, deeper, more secure, more precise. To summarize that you could say: better :D

---

### Post by Vico Vicario on 2009-02-12
> **whoop said:**
> How to convert the file system to ext4 (in jaunty)!
Here's what I did:

Booted jaunty livecd on a system running jaunty and ext3 (on /dev/sda1), opened a terminal:
```

sudo bash
tune2fs -O extents,uninit_bg,dir_index /dev/sda1
e2fsck -pf /dev/sda1
mount -t ext4 /dev/sda1 /mnt
nano /mnt/etc/fstab

```

In fstab I changed "ext3" to "ext4" for the partition I converted (and saved the changes)

Just want to add step 0. If you have upgraded from Intrepid you might have an old grub version. Check /boot/grub/installed-version . You need at least 0.97-29ubuntu47. If your version is older, do a "sudo grub-install /dev/DEV" before converting the filesystem.

V.

---

