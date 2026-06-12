---
title: "Can I recover XP partition formatted to ext3?"
date: 2007-03-04
forum: Installation &amp; Upgrades
---

### Post by kidamnesiac on 2007-03-04
Help please!

I was manually editing the partition table and, I dont know why having performed similar operations over a dozen times now, the partition editor decided to reformat the windows partition to ext3 filesystem. Is there anyway I can get my data back?

I did not do a backup as I have never had a problem doing partition editing or linux installations before. 

Any help in pointing me in the right direction is appreciated.

---

### Post by steveyos666 on 2007-03-04
This is why I always back up my stuff to my ipod :/

---

### Post by Henry Rayker on 2007-03-04
I just wanted to point out that I doubt the partition editor "decided" anything. More than likely what happened is you clicked the wrong partition or somesuch.

Now that that's out of the way, I'm really not too sure about recovering an NTFS system from an ext3...the drive has been formatted, and you'd likely have to format back to NTFS just to have any chance...and then the likelyhood that you'll get much out of the drive sounds fairly slim to me =\

---

### Post by kidamnesiac on 2007-03-04
:/

the reason i ask is because i dont think the partition was completely formatted, just the file system extensions (if that makes sense). If I thought it was totally wiped I wouldn't ask but I'm fairly sure the data is still there, I just can't see it.

It also says all of the space is free, but could that be just because it is expecting ext3 data?

---

### Post by kidamnesiac on 2007-03-04
what I think happened is that ubuntu wanted to put grub there, when i looked at it later it was labelled boot

I have tried formatting it back to ntfs but it did not instantly fix the problem and now i am hunting boards to find help.

thanks

---

### Post by steveyos666 on 2007-03-04
Maybe if you put the hard drive into another computer and use a data recovery program it'd do something...

Other than that all I can say is buy an iPod, or one of those sidekick cell phones there all the kids go crazy about :o

---

### Post by kidamnesiac on 2007-03-04
To anyone who has a similar problem in the future:
[http://servers.linux.com/article.pl?sid=06/08/21/1558230&from=rss](http://servers.linux.com/article.pl?sid=06/08/21/1558230&from=rss)

is recovering the formatted partition now, it's going to take weeks to sort through but at least i get them back :)

---

