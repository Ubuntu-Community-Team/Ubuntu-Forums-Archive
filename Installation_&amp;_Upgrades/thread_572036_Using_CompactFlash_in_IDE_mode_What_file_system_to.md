---
title: "Using CompactFlash in IDE mode: What file system to use?"
date: 2007-10-10
forum: Installation &amp; Upgrades
---

### Post by Fox5 on 2007-10-10
Hey all,

I'd like to use a compact flash drive with an IDE adapter in my thinkpad x41t (harddrive died and the 1.8" replacements are too expensive and slow, so it seems like a worthwhile alternative).

I have a RiData 16GB compact flash card rated for 100,000 cycles and supports UDMA4.

I'm wondering what file system I should format it is. I've tried looking on the internet, but the results I've seen have been all over the place:
Simpler file systems, such as fat32 or ext2 since they avoid journaling and most more advanced file systems are made around disk systems.

JFFS2 because it's made for flash systems, at the same time though it sounds slow and unwieldy and won't work right with the IDE mode of compact flash drives.

YAFFS simply recommended because it's a flash file system that isn't slow.

Reiser4 as it has attributes similar to JFFS2 apparently and avoids journaling.

ReiserFS because it's journaling should work well with flash drives? (I know JFFS2 journals, so I'm assuming there's nothing wrong with journaling)

Or that it simply doesn't matter, use any file system, preferrably as simple as possible.

Compact flash cards have built in IDE controllers that are supposed to have some sort of wear management, but once again ideas about this have been all over the place. Some say that most manufactuers don't even bother to put in wear leveling since the cards are just used for taking photos and some say that dumb but effective enough wear leveling schemes are used (optimized around fat). Some ideas say go fat to match the wear leveling schemes, some say that the wear leveling schemes suck and to use JFFS2 or YAFFS for added bonus, some say that would be worse, and some say Resier is the perfect file system for flash memory hidden behind an ide interface.


So, can anyone come up with a conclusive recommendation for a file system? Or at least tell me whether journaling is good or bad for flash.

Thanks,
Paul

---

### Post by fwendt on 2008-02-17
Hi fox5. What did you end up with? Did it work out nice? I have a similar situation (2,5" SATA from Transcend, 32 GB SSD MLC flash device). I just did a block copy from the previous disk's partitions/filesystems (ext3) and it works, but it's one of the slowest flash devices around (read/write at 32/16 MB/s) and too often it just stalls my system trying to catch up on IO operations.
I'd love to hear what you use and how it's working for you.
/ Fredrik

---

### Post by Fox5 on 2008-02-17
I actually ended up using a RiData compactflash device. It was pretty bad, write speeds hovered around 1-2MB/s, which made it perform very poorly (though I suppose this could have been handled the same way the pen drive linux projects handle it, mount a read only file system), but more importantly, it died after only a few days of use.

However, other people have been having good luck with the sandisk ultra 3 and 4 series. Most other compactflash cards have ended up too slow on write speeds to be usable, though there are others out there with decent speeds.

However, your SSD at 32/16 MB/s is pretty fast compared to most compact flash devices, assuming that's measured performance and not just manufacturer stated. (use hdtach) Fastest are around ~45/35 MB/s. This is still pretty slow compared to some 2.5" drives that are available, so unless you really need the lowest power device available or are stuck with a device that uses a 1.8" drive, I don't think I could recommend a flash drive for a laptop at this time.

No conclusion was ever reached about file systems, however. HDTach seems pretty immune to file system type so its reported performance results didn't really change. Some file systems did just "feel" slower than others though, such as JFS.
Ext3 MIGHT be bad for the life span of a flash device due to its full journal support, but on the other hand current flash devices (especially SSDs made for longevity) are likely to be robust enough to survive anyway. No idea why my Ridata card failed so quickly, as others aren't having problems with their devices. (most popular are sandisk extreme 3 or 4 and lexar 300x, I've heard of a few reports of people using ssds as well)

---

### Post by fwendt on 2008-02-17
Thanks for all of your answers. It pretty much is what I expected, though one part of my brain was convincing me that I should hope for more ...

hdparm -t /dev/sdaX says it reads at 23 MB/s under normal (non-)load.

One thing I will try before putting the old noicier, more power demanding but faster disk back in is to try some filesystem other than ext2/3 and see if O log(n) on file/path operations helps. (It's that irrational part of the brain talking again I guess.)

Really thanks for your answer. If you have better sources on this topic (better than ubuntu forums) I'd be thankful if you'd share that info too.

Thanks / Fredrik

---

### Post by Fox5 on 2008-02-17
As I said, hdparm (incorrectly said it as hdtach) doesn't seem to change results based on file system. From my understanding, it pretty much just reads/writes one large file so the advantages of a file system don't get shown. There are full harddrive test suites available for linux, it wouldn't be a bad idea to test one of those instead of relying on hdparm's rather dumb tests.
Also, I think hdparm has an option to test writes as well, so you should try that as well. Most flash devices can put out decent read speeds, but are horrible at writes.

Since you've already tried ext3, I'd try ext2 (no journaling to slow down writes) as well. Besides that, ReiserFS may work better. JFS and XFS are options I suppose, but from what I've read about them they seem more optimized for drives with fast sequential writes.
Reiser4 sounds like the ideal file system for a flash based device, but you'd have to compile your own kernal to get access to it.
JFFS and YAFFS aren't really recommended due to the IDE controller sitting in between the flash memory and the computer, they're really more designed around having direct access to the flash memory.

As for a better option, you should check out this thread:
[http://forum.thinkpads.com/viewtopic.php?t=41568](http://forum.thinkpads.com/viewtopic.php?t=41568)

It's at a site for thinkpads, and a few thinkpads use terribly slow 1.8" drives, so the idea of using flash based alternatives gained a lot of attention. Some users are successfully using flash drives with notable improvements over the 1.8" drive, but like I said a fast 2.5" drive is faster than any currently affordable flash based option, with far more storage too. A surprising number of people even got the flash drives working with windows, though it's not as plug and play as ubuntu is.

---

### Post by fwendt on 2008-02-17
Thanks once again. I'll leave my trail of findings here too, which basically goes through Kevin Burton's findings and blog notes suc has [http://feedblog.org/2008/02/01/random-write-performance-in-ssds/](http://feedblog.org/2008/02/01/random-write-performance-in-ssds/)
I'll try to see if I can get nilfs working.

I'll also ask at the linux-thinkpad mailing where I've been a subscriber for some time and not yet seen a single post on the topic.

Regarding testing and some kind of metrics I'll let bonnie++ have a go, and optionally [http://sysbench.sourceforge.net/](http://sysbench.sourceforge.net/) as well.

Oh, and mounting with noatime option really increases the overall performance _feel_.

---

