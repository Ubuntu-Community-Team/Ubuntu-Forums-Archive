---
title: "The New Ext4 FS Works Great!"
date: 2009-04-06
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by kevpan815 on 2009-04-06
The New Ext4 FS Works Great!

---

### Post by damis648 on 2009-04-06
Alrighty. :popcorn:

---

### Post by Yashiro on 2009-04-06
It doesn't.

---

### Post by SuperSonic4 on 2009-04-06
So far so good here. Didn't lose any meaningful data when my brother tripped the fuse either :]

---

### Post by 4Orbs on 2009-04-06
running wine and ext4. Now I can actually defeat Duriel. wtf?

---

### Post by MysticGold04 on 2009-04-06
One thing I noticed... It let my old AMD system boot in half the time of ext3 in Hardy... (which I still have on a separate drive)

---

### Post by go7Ul1ai on 2009-04-06
I love how fast it does a routine file system check, on Ext3 it took ages, not on Ext 4 it takes a second or so :)

Awesome :D

---

### Post by Polygon on 2009-04-06
it works great, until your system crashes and you lose data. Then its not so great.

---

### Post by Nullack on 2009-04-06
Yeah it works but the application side of this new file system has a bunch of problems that will result in zeroed out files when the system crashes.

---

### Post by BGFG on 2009-04-06
> **Nullack said:**
> Yeah it works but the application side of this new file system has a bunch of problems that will result in zeroed out files when the system crashes.

I'll save my complaints for when i crash then :P, so far, speed and stability...

---

### Post by 3togo on 2009-04-06
your mean the faster boot up is because of Jaunty as a whole or merely attributed by ext4?
> **MysticGold04 said:**
> One thing I noticed... It let my old AMD system boot in half the time of ext3 in Hardy... (which I still have on a separate drive)

---

### Post by krazyd on 2009-04-06
> **Nullack said:**
> Yeah it works but the application side of this new file system has a bunch of problems that will result in zeroed out files when the system crashes.
Actually, the patch fixing this has been [backported to jaunty]("https://bugs.launchpad.net/ubuntu/jaunty/+source/linux/+bug/317781/comments/173").

---

### Post by razor7 on 2009-04-06
Hello...i downloaded the ubuntu 9.04 dayly live-cd image from cdimage.ubuntu.com using rsync today and when installing and using manual partition mode...there is no ext4 option to select partition format

anyone knows if ext4 will be rejected on jaunty final release?

I have filled a bug report here [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/355440](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/355440)

Thanks a lot!

---

### Post by psyke83 on 2009-04-07
> **razor7 said:**
> Hello...i downloaded the ubuntu 9.04 dayly live-cd image from cdimage.ubuntu.com using rsync today and when installing and using manual partition mode...there is no ext4 option to select partition format

anyone knows if ext4 will be rejected on jaunty final release?

I have filled a bug report here [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/355440](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/355440)

Thanks a lot!

The daily images aren't always guaranteed to be installable, especially when not close to a particular milestone (alpha, beta, rc, release). Perhaps it's just bad timing (and luck) on your part.

---

### Post by razor7 on 2009-04-07
ok...thanks!

---

### Post by Polygon on 2009-04-07
> **razor7 said:**
> Hello...i downloaded the ubuntu 9.04 dayly live-cd image from cdimage.ubuntu.com using rsync today and when installing and using manual partition mode...there is no ext4 option to select partition format

anyone knows if ext4 will be rejected on jaunty final release?

I have filled a bug report here [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/355440](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/355440)

Thanks a lot!

maybe it has, like i said earlier, the loss of data thing is really quite bad, i have already lost a few files......luckily were only screenshots but none the less..

---

### Post by Lorenz on 2009-04-07
So that data loss bug has been fixed?
I'd be really temtped to make the change!

---

### Post by razor7 on 2009-04-07
I have installed jaunty in my aspire 4520 laptop and there is no data loss, also I have mounted 2 NTFS partitions...

I have seen all the bug reports and Im really thinking to drop ext4 until is more stable and relyable, but the speed increment is so significant that Im having problems to decide...jajaja

Best regards!

---

### Post by Takmadeus on 2009-04-07
> I have seen all the bug reports and Im really thinking to drop ext4 until is more stable and relyable, but the speed increment is so significant that Im having problems to decide...jajaja


Wow, exactly what I was thinking.... hope they fix up things anytime soon ;)

---

### Post by Sockerdrickan on 2009-04-07
I've lost files too -_-

---

### Post by Coplen on 2009-04-08
It works well for me. I wish the people here mentioning file data loss paid attention to that bug being fixed already instead of carrying on. ;)

---

### Post by amano on 2009-04-08
> **krazyd said:**
> Actually, the patch fixing this has been [backported to jaunty]("https://bugs.launchpad.net/ubuntu/jaunty/+source/linux/+bug/317781/comments/173").

I don't think that this patch will work wonders with all kinds of data loss. Theodore T'so mentioned that userland applications will have to be fixed as well to become reliable again. 

The patch from above will just remove some cornercases when both states of the file will be zero-ed. The state from before the write and the current state.

---

### Post by MacUntu on 2009-04-08
> **amano said:**
> The patch from above will just remove some cornercases when both states of the file will be zero-ed. The state from before the write and the current state.

Wasn't that the main problem? Files being gone - no old state, no new state (eg. config files got zeroed leaving the machine in an unusable state). 

The data loss itself isn't or shouldn't be surprising since the FS uses delayed allocation - the longer time frame only increases the amount of new data not written to disk.

Having the first fixed is enough for me.

---

### Post by amano on 2009-04-08
That's fine. I would be upset losing a saved file because of delayed allocation personally. Thus I will wait until most of the programs are updated to properly use fsync(). Not even GVFS/GIO does that at the moment.

---

### Post by habtool on 2009-04-08
Disable delayed allocation will be short term workaround:

Info on adding nodelalloc and testing if it worked:

at a terminal type: mount

before
/dev/sdb2 on / type ext4 (rw,relatime,errors=remount-ro)

after
/dev/sdb2 on / type ext4 (rw,relatime,errors=remount-ro,nodelalloc)

(To enable no delayed allocation...)
nodelalloc added in FSTAB
# / was on /dev/sdb2 during installation
UUID=e3b96b25-6633-4744-9bd9-4c6428acfcbc / ext4 relatime,errors=remount-ro,nodelalloc 0 1

---

### Post by amano on 2009-04-08
Scanning through the 2.6.30 changelog was interesting:

They just updated ext3 to use the "writeback" mount option by default and improved the fsync() speed for ext3.

Thus over the the next cycle the gnome programs and the GNU userpace tools will all be updated to use fsync() extensively to avoid data-loss with ext4/btrfs in the future.

This would be a big speed hit for ext3, thus they changed ext3 to a less secure mode (data without being fsynced will be written just every 5 seconds, while being written instantly now).

For now I would recommend to stay with ext3 until all the fsyncs will be in place and upgrade to ext4 for koala because ext3 will be equally less secure then, but most prgrams will have made the transition to use fsync() at that time.

Now:
ext3 --> data written instantly by default
ext4 --> data written after up to 120 seconds
ext4 (only few programs using the fsync now) --> data written instantly

Then:
ext3 --> data written after up to 5 seconds
ext3 (with most programs using the fsync then) --> data written instantly
ext4 --> data written after up to 120 seconds
ext4 (with most programs using the fsync then) --> data written instantly

It will be important to have the Ubuntu team make sure, that all default programs migrate to use the fsync() call for Karmic. Most importantly to have GVFS/GIO use those calls (the patches do exist already).

---

### Post by MTGap on 2009-04-08
Ext4 isn't bad at all, no data loss at all and I've had multiple crashes (mainly due to heavy cpu usage from tivodecode) For all of you not being able to find the option for ext4 you have to go to manual in the partition manager select your drive and right click it where you can format it differently, such as ext4. 


I'm running it on an external hard drive as well which makes problems more possible, I've even accidentally pulled out the usb cord during bootup. No data loss there... lol Booted up just like normal, not to mention booting up faster than ever before. You'd be silly not to use ext4 with Jaunty.

---

### Post by n3had on 2009-04-08
> **MTGap said:**
> Ext4 isn't bad at all, no data loss at all and I've had multiple crashes (mainly due to heavy cpu usage from tivodecode) For all of you not being able to find the option for ext4 you have to go to manual in the partition manager select your drive and right click it where you can format it differently, such as ext4. 


I'm running it on an external hard drive as well which makes problems more possible, I've even accidentally pulled out the usb cord during bootup. No data loss there... lol Booted up just like normal, not to mention booting up faster than ever before. You'd be silly not to use ext4 with Jaunty.

should i really go for it???????? dying to try it out ..

---

### Post by megamania on 2009-04-08
> **Polygon said:**
> it works great, until your system crashes and you lose data. Then its not so great.
I installed Jaunty with an EXT4 root and EXT3 home. 

I thought it could be a good compromise in order to reduce the possibility of data loss... but I'm not sure it makes sense.

---

### Post by MTGap on 2009-04-08
Well just back up your files somewhere... It isn't that unstable as people make it appear to be. Just be cautious if your keeping important files on your computer, I like Jaunty so far only for the reason that it has ext4. Without it, it wouldn't be nearly as fantastic.

---

### Post by MysticGold04 on 2009-04-08
> **3togo said:**
> your mean the faster boot up is because of Jaunty as a whole or merely attributed by ext4?

Not sure which, but it sure made a difference somewhere!

---

### Post by razor7 on 2009-04-08
The ext4 is back again in the cdimage rsync repo!

I think that in the next 15 days remaining to have final Jaunty, ext4 will be fixed, if not, there will be a jaunty patch in the middle term to karmic, maybe Ubuntu 9.04.1

---

### Post by razor7 on 2009-04-08
> **3togo said:**
> your mean the faster boot up is because of Jaunty as a whole or merely attributed by ext4?

The speed up is sensible, so I think yes.

---

