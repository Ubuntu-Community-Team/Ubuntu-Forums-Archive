---
title: "Installing Ubuntu not working!"
date: 2007-10-26
forum: Installation &amp; Upgrades
---

### Post by It_Was_Luck on 2007-10-26
Okay so I have a ehh, 2004 Dell computer with an 80GB HD. I burned myself a copy of Ubuntu (the newest one) tried it out on the liveCD and loved it... So I go to downloading, and I get to the partion editor.

Well right of the bat I have 3 primary partions my NFTS, main partion which is about 75GB, then I have a FAT16 thats about 5GB and has used like all of it, but I have no idea what a FAT16 is needed for, then I have a FAT32 which has about 400MB of space and only used about 30MB of it... also I have no idea what it does.

So I edited my NFTS partion to have 10 less GB, so I can use 8 for ubuntu and 2 for the swap thingy I need. So I do that, and I have my 10GB floating around, so I go and create on EXT3 about 8GB for ubuntu, well after it does that, it no longer will let me use any of my extra 2GB, it says "unallocated" in the spaces. 

So i went into GParted and figured out that you can only have 4 primary partitions... my NFTS, my FAT16 & 32 (which I have no idea what they do...) and now my EXT3 for unbuntu... So I'm stuck, I don't have a swap partition. 

So pretty much I was wondering if anyone knew what the FAT16 and Fat32 partions are used for and if i can SAFELY delete one so I can make the swap partition for ubuntu...

---

### Post by Fire_Chief on 2007-10-26
If the Dell has not been reformatted since coming from the factory, then one of those partitions is probably for factory image restore (most likely the FAT32). The FAT16 partition may be a diagnostics partition (especially if you see a message during boot about press such and such key for diagnostics).
To be sure, you should boot back into Windows and use Disk Manager to view the partitions. They often have labels in Windows that will clue you in on their use.

If you don't care about ever restoring the original Windows installation from Dell, then you should be able to safely delete that partition and reallocate it for your needs.

---

### Post by It_Was_Luck on 2007-10-26
Okay using a program called Acronis Disk Dirrector Suite it gives a little info on each.

On the Fat16 it says this: FS: FAT16 Partition: 0xDE (EISA configuration)

And on the Fat32 it says this: FS: FAT32 Partition: 0xDB (Concurrent DOS, CTOS)


...

---

### Post by Fire_Chief on 2007-10-26
On a side note, while running with a swap partition is recommended, it is not required. I have 2GB of RAM in my laptop and don't use a swap partition. The system runs very well but I also don't run so many apps at once as to come close to maxing out the RAM in the system. Your needs may be different but it's just a thought.

---

### Post by HermanAB on 2007-10-26
Please do make a swap partition.  You may not need it, but when you do, you'd wish you had one...

Also, do make a /home partition.  The reason being that you normally keep all your data in /home, so if you wish to upgrade/re-install, then you can do so without erasing all your data.

Cheers,

Herman

---

### Post by logos34 on 2007-10-26
It_Was_Luck,

You don't actually have to delete anything to make room...Just create an [extended]("http://tldp.org/HOWTO/Partition/partition-types.html#logical") partition out of the 10gb space and put /, /swap and whatever else inside as logical partitions

---

### Post by It_Was_Luck on 2007-10-26
So can I create the extended partition from GParted or the partition editor in the installer?

EDIT: Okay I noticed that in GParted I can create a extended partition but then I can't mark it as a swap... So how do I create a extended partition of a swap.

---

### Post by It_Was_Luck on 2007-10-26
Bump..

I'm sitting in front of my computer eating a sandwich while I wait for a reply...

EDIT: Okay I know I bumped but I figured this out.. I think.

Okay so I used GParted to create my partitons. I created a extended partion of my 9.81GB I want for Ubuntu. As you can see right under it I have the 8GB ext3 file, thats for ubuntu...  Then below that I have the 1.82GB for the linux-swap.
 If I partition it like this can I go into the installer and just put a mouse pint on the ext3 one?

In other words, will this work?

[[IMG]http://img207.imageshack.us/img207/2796/screenshotng0.th.png[/IMG]](http://img207.imageshack.us/my.php?image=screenshotng0.png)

(click on the photo for a larger image)

---

### Post by logos34 on 2007-10-26
Yes, that's it!  Perfect.  

Start installer and choose 'manual'.  
-Put root on sda5 (~8gb) with mountpoint '/'
-swap on sda6 with mountpoint '/swap'

(sorry, for the delayed response)

---

### Post by It_Was_Luck on 2007-10-26
I heard someone saying something about a /home partition to... 

What does this do and is it worth it?

---

### Post by logos34 on 2007-10-26
yeah, seaprate /home is way to go, although you don't have much room to work with...maybe shave off a couple of gigs from root and a half gig from swap and give it to /home.

---

### Post by shamusl on 2007-10-26
With 8 gigs, i don't think he should bother, but thats just me.

---

### Post by logos34 on 2007-10-26
yeah, it's almost not worth it. 

the basic idea:

> /home partitions are wonderful things. It would be the equivalent of Windows of having a partition that was the C:\Documents and Settings folder. That would include My Documents, My Pictures, My Music, and all your hidden settings, too. Likewise, a /home partition in Ubuntu has all your settings. Ordinarily, it would have your files, too, but in the scenario pictured above, your files would live in the FAT32 partition.

The benefit of having a separate /home partition? Well, it means you can reinstall Ubuntu as many times as you'd like and do a clean install (instead of an upgrade) when a new version of Ubuntu comes along. When you first start using Ubuntu, you usually have no idea what you're doing, and you end up breaking something. Now, if you're a veteran, you know how to fix whatever you've broken. If you have a lot of time, you could probably ask around and find out how to fix it. Sometimes, though, it just seems easier to reinstall (the installation takes anywhere from 20 minutes to an hour), and not having to re-do all your settings is a good thing. 

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://img379.imageshack.us/my.php?image=partitioning4mz5.png](http://img379.imageshack.us/my.php?image=partitioning4mz5.png)

---

### Post by It_Was_Luck on 2007-10-26
Yeah... maybe with my next computer I'll do that cause I plan on getting more storage next time.

Thanks a lot guys and I'll tell you how it goes.

EDIT:

Okay so i set the ext3 partition's mouse point to "/" then I pressed continue and I got this message...
[[IMG]http://img145.imageshack.us/img145/2098/screenshot1oc4.th.png[/IMG]](http://img145.imageshack.us/my.php?image=screenshot1oc4.png)

---

### Post by It_Was_Luck on 2007-10-26
Bump... its like 8 where I live and I would like this to get installed by tonight...

---

### Post by It_Was_Luck on 2007-10-26
help!

---

### Post by logos34 on 2007-10-26
thought you could take it from there...umm, never seen that warning, it's complaining about the FAT16 or 32 partition, not the /...I think you can safely ignore it.  Tick the 'format' box for / sda5.

---

### Post by It_Was_Luck on 2007-10-26
trust me I thought I could to, but my computer isn't new, I have files on windows xp still and I couldn't afford to lose them, so I had to confirm.

i wnet back checked the format box, press okay I got the message, ignored it then it started installing...

---

