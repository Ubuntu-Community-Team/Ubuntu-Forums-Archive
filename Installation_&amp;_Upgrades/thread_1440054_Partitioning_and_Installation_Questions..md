---
title: "Partitioning and Installation Questions."
date: 2010-03-27
forum: Installation &amp; Upgrades
---

### Post by Sneux on 2010-03-27
Well hello all, im very new to the forums and Linux. I had planned to start off with SlackWare but I decided to go to Ubuntu since Back|Track 4 is based on it. Now my problem. I wish to get rid of this old Windows XP and go to Ubuntu I have burnt the ISO on a DVD and such and am ready to format and switch but im not sure how or if I should partition my disks at all. This is a very old PC, 2003 HP Desktop with around 22 GB on its HDD and it works really well but I have no idea at all how to or if I should partition my disk here is an image for reference of how I have it now.  I want to make sure I have enough room on my HDD(I suspect since WinXP does Ubuntu will haha but I still want to make sure I don't fudge up at all.)  Also could you explain how i should part my disks for optimal performance?  Thank you for all the help.  EDIT: Picture for reference. [http://i768.photobucket.com/albums/xx325/Sneux_Corten/HDD.jpg](http://i768.photobucket.com/albums/xx325/Sneux_Corten/HDD.jpg)

---

### Post by srix on 2010-03-27
I guess there's no "one right method", but I like to make sure that system files are kept separate from my data files. I would suggest creating /, /usr and /home partitions at the very least. That way you can always upgrade/reinstall the system while keeping your data partition intact. Depending on how much software you are likely to install and experiment with, you can decide how much to reserve for / and /usr. I would think a minimum of around 1+2 GB would be good for / and /usr. You'd also have to have a swap partition roughly the size of your installed RAM.

HTH...

---

### Post by Sneux on 2010-03-27
Well I have around 632 RAM and I seriously know nothing about Ubuntu yet so I guess I need to read up some more haha.

---

### Post by srix on 2010-03-27
That would certainly help :) All the best, and have fun with Ubuntu!

---

### Post by gordintoronto on 2010-03-27
I can't see any benefit to having a /usr partition.  If it were my system, I would have 6 GB for root (/), 700 MB for swap and the rest for /home.

During installation you are prompted to partition your hard drive, and you need to select the advanced option to have separate root and home partitions.

---

### Post by srs5694 on 2010-03-27
> **gordintoronto said:**
> I can't see any benefit to having a /usr partition.  If it were my system, I would have 6 GB for root (/), 700 MB for swap and the rest for /home.

There are several potential benefits:


[list]
[*]You can probably mount /usr read-only most of the time, which has security and safety benefits.
[*]You can use different filesystems on the different partitions -- say to use Btrfs for its snapshotting features on one, or to use ReiserFS for its small-file performance on one.
[*]Completely filling /usr won't fill root (/) and therefore won't impede your ability to log in or do maintenance. (Of course, this advantage is at least partly offset by the fact that you'll be more likely to completely fill /usr than if you devoted equal space to a single root partition that includes /usr; and ext2/3/4 filesystems include a reserved space percentage for this reason, if you use one of them.)
[*]You could set different quotas on these filesystems, although this would probably not be very meaningful unless you enabled users to write to some directory of /usr for some reason.
[/list]


Personally, I usually do set aside a separate /usr partition, and often others, too (/usr/local, sometimes /opt or /var). Some people like using a separate /tmp partition. Of course, the more partitions you separate like this the more likely it becomes that you'll find they're badly mis-sized in the future, requiring resizing or ugly workarounds. I generally advise new users to use root (/), /home, and swap, and to separate others only if they've got a compelling reason to do so. Experienced users are more likely to be able to get the sizes right for more partitions.

---

### Post by gordintoronto on 2010-03-28
I like to *use* my computer, not mess around with mounting partitions and experimenting with different filesystems. Oh, all right, I do mess around with different applications. Which is why my root is huge...

---

### Post by srs5694 on 2010-03-28
You may consider the benefits I posted to be pointless "mess[ing] around," but not all people do. Those benefits are very real and important on some installations. Granted, many of those systems are much bigger and more professional than is common for Ubuntu home desktop installations, but they certainly are real, and you should be able to "see [the] benefit" of them in the abstract, even if the benefits are unimportant to you personally. Note that my own concluding recommendation did *not* include a separate /usr, except by implication of readers thought it would provide benefit *for them.* As is common in computers, one size does not fit all.

---

### Post by gordintoronto on 2010-03-29
> **srs5694 said:**
> You may consider the benefits I posted to be pointless "mess[ing] around,"...

Exactly right.  For example, when I connect a device or insert media, it is always automatically mounted.  Why would I have to learn about mounting when "it just works"?

I read questions from people for whom it doesn't "just work," and I'm puzzled: what did they do wrong?

I would like to hear other perspectives.

---

