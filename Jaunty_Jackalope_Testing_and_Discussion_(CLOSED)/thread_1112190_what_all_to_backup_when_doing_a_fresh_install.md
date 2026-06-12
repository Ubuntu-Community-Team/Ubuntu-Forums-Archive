---
title: "what all to backup when doing a fresh install?"
date: 2009-03-31
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by nightshade209 on 2009-03-31
When i upgrade to Jaunty, i intend to use the ext4 filesystem. Does that mean i will have to do a fresh install? Also, in that case, what all data do i need to backup? Will only my home folder suffice?

---

### Post by anjilslaire on 2009-03-31
Yes you will need a fresh install, as the drive will need to be formatted as ext4. In most cases, backing up /home will usualy do, unless you have any media files in another location.

---

### Post by philinux on 2009-03-31
You can convert ext3 to ext4 but the process is not all plain sailing.

You need to post in here.

[http://ubuntuforums.org/forumdisplay.php?f=352](http://ubuntuforums.org/forumdisplay.php?f=352)

see this thread.

[http://ubuntuforums.org/showthread.php?t=1104822](http://ubuntuforums.org/showthread.php?t=1104822)

In fact I'm running Jaunty but I'm staying clear of ext4 for now.

---

### Post by James_Lochhead on 2009-03-31
> **philinux said:**
> In fact I'm running Jaunty but I'm staying clear of ext4 for now.

I have had no problems with ext4 so far. Bring on BTRFS tho :-D

---

### Post by hyper_ch on 2009-03-31
there's a serious bug with ext4 that can lead to dataloss. If you're willing to accept the risk, go ahead.

---

### Post by nightshade209 on 2009-04-02
> **hyper_ch said:**
> there's a serious bug with ext4 that can lead to dataloss. If you're willing to accept the risk, go ahead.

What bug precisely? And how serious is it? Will it be corrected by the time Jaunty actually comes out?

---

### Post by FuturePilot on 2009-04-02
> **hyper_ch said:**
> there's a serious bug with ext4 that can lead to dataloss. If you're willing to accept the risk, go ahead.

> **nightshade209 said:**
> What bug precisely? And how serious is it? Will it be corrected by the time Jaunty actually comes out?

The data loss problem has been fixed
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/317781/comments/154]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/317781/comments/154")

There's no reason to reinstall. Ext3 can be converted to Ext4

---

### Post by philinux on 2009-04-02
> **nightshade209 said:**
> What bug precisely? And how serious is it? Will it be corrected by the time Jaunty actually comes out?

The bug was not a bug LOL but a feature.

[http://www.h-online.com/open/Ext4-data-loss-explanations-and-workarounds--/news/112892](http://www.h-online.com/open/Ext4-data-loss-explanations-and-workarounds--/news/112892)

But as Future points out the "bug" got fixed.

---

### Post by olskar on 2009-04-02
Remember to press Ctrl+H in your homefolder if there is something hidden you want to keep like chathistory or something :) Beside that I don't backup anything outside my homefolder

And use the backupfunction in evolution if you are using that, backuping your bookmarks in firefox can be nice to, for that I use foxmarks :)

---

### Post by phenest on 2009-04-02
> **FuturePilot said:**
> There's no reason to reinstall. Ext3 can be converted to Ext4

If I convert ext3 to ext4, will I get the full benefits of ext4?

---

### Post by FuturePilot on 2009-04-02
> **phenest said:**
> If I convert ext3 to ext4, will I get the full benefits of ext4?

The only thing that will be different is that existing files won't use extents, only new files will. However this would only be temporary because once the Ext4 defragging tool is available, it will allow you to move existing files over to using extents. Other than that, you will have all the benefits of Ext4.

---

### Post by phenest on 2009-04-02
> **FuturePilot said:**
> ...once the Ext4 defragging tool is available...

Defragging tool? Will it need it? I thought that these filing systems were intelligent enough to not need such things.

---

### Post by FuturePilot on 2009-04-02
> **phenest said:**
> Defragging tool? Will it need it? I thought that these filing systems were intelligent enough to not need such things.

Regardless of the type of filesystem, it will eventually become fragmented. AFAIK there is no filesystem that is perfect and that does not fragment. However, the Ext and other Linux filesystems are particularly resistant to fragmentation. With that said, defragging Ext4 is not something that you would have to do every week like with other operating systems. The Linux filesystems only become unacceptably fragmented after very long periods of time, and when I say a long time I'm talking years.

Here is a quote from [this]("http://ubuntuforums.org/showthread.php?t=169551") thread.
> Q: A defragger? For Linux? Are you crazy?
A: No, I certainly am not. Under certain circumstances, even the most fragmentation-resistant filesystems get fragmented. Don't believe me? Look around with defrag. Whether or not filesystem performance is affected can be debatable at times, though I personally have to say that when a 300MB torrent is split into 5000 fragments, read speed is drastically affected.


---

### Post by nightshade209 on 2009-04-03
> **FuturePilot said:**
> There's no reason to reinstall. Ext3 can be converted to Ext4

That means it can be done with a regular upgrade? I dont need to backup?

---

### Post by FuturePilot on 2009-04-03
> **nightshade209 said:**
> That means it can be done with a regular upgrade? I dont need to backup?

Yes.

---

### Post by nightshade209 on 2009-04-04
Ok thanks a lot everyone! I was worried about the whole backing up thing... But, problem solved! :D

---

### Post by hyper_ch on 2009-04-05
you always need backups... what if your drive decides to stop working tomorrow. All your data is gone if you don't have a backup.

---

### Post by novafluxx on 2009-04-05
I'd say try to convert the file system just for the learning experience, then when Jaunty final is released, do a fresh install. Always make/keep backups however.

---

