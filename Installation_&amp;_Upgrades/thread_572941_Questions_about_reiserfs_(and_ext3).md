---
title: "Questions about reiserfs (and ext3)"
date: 2007-10-11
forum: Installation &amp; Upgrades
---

### Post by musther on 2007-10-11
I'll be re-installing in a few days when 7.10 is out, and am wondering about moving to reiserfs.  At first I had no major reason, ext3 has served me well, but nevertheless I began investigating...  

Basically, what it seemed to come down to is:

Ext3 is tried and true, solid and reliable, but usually slower than reiserfs, especially with lots of small files, and reiserfs is less robust.  Reiserfs also has less overhead (in terms of space, ext3 seems quite wasteful).

But what I didn't find, were any reasons for why (or even explanations of how) reiserfs is less robust, so is it really?

One other thing which has been nagging at the back of my mind is the regular fsck which occurs on ext3 filesystems, but not on reiserfs, what's the reason for the difference, and is it this that somehow makes reiserfs less robust?  Also, if the filesystem is marked clean, and is a journaled system, what is the purpose of the periodic fsck?

I hope there's some fs guru around who can explain some of these interesting points to me...

Cheers.

---

### Post by dabl on 2007-10-11
When I first installed Kubuntu Dapper a year ago, I didn't know any better and my self-research suggested that reiserfs was pretty fast, so that's what I set up on my new system.  I've been running it ever since.

I don't know why you say "less robust" -- I think the opposite is true.  In a year, I've been hit twice with a power failure/sag that was faster than my UPS, and caused a crash.  The reiserfs system re-plays the journals on every boot, and both times it repaired itself and I had zero issues with data corruption or loss. It does make a very slow boot, so maybe if I used a laptop I'd go with ext3 to have the faster boot, but on my desktop I feel I'm getting the best performance and reliability with reiserfs.

BTW, some Linux distributions are now recommending reiserfs in their installation guidance.

:popcorn:

---

### Post by musther on 2007-10-11
Thanks for that.  

The only reason I said reiserfs is less robust is because that's what I've been lead to believe by the 'reviews' comparing them - as I said, I haven't actually found any evidence.

When you say reiserfs boot times are long, do you mean in general or just when it has to replay the journal due to an unclean state?

Yes, some distributions are using reiserfs by default, (according to wikipedia - Slackware, Xandros, Yoper, Linspire, GoboLinux) but it's also interesting to note that SuSE has dropped reiserfs for ext3, and many of the large distros (I guess Ubuntu fits there too) are firmly sticking with ext3.

To be honest I can't get a straight answer anyway, maybe nobody really knows.  Thank you for telling me about your experience though.

What I find interesting is that most reviews or forum posts or blogs about reiser v ext3 conclude that reiserfs is faster, stable, and has less overhead, but then go on to give the impression that ext3 is still a better choice unless you're willing to be a little more risky...   and I just don't see why.

I wonder if I'll ever get to the bottom of this!  :-)

---

### Post by Steveway on 2007-10-11
Yes Reiser really tends to break very easily.
It is all written down in Wikipedia:
[http://en.wikipedia.org/wiki/ReiserFS#Criticism](http://en.wikipedia.org/wiki/ReiserFS#Criticism)

---

### Post by jdfreshwater on 2007-10-11
I think the main reason for a change to ext3 for many is the upgrade path was uncertain for reiser.  At this time I  the maxium filesystem size for reiser is 16 TB and 32 TB for ext3.  With more storeage coming out, it may be soon before hard drives hit this limit.

---

### Post by dabl on 2007-10-11
> **Steveway said:**
> Yes Reiser really tends to break very easily.



Huh? It doesn't say that ... doesn't say anything like that!  :confused:

It says this:

> Some directory operations (including unlink(2)) are not synchronous on ReiserFS, which can result in data corruption with applications relying heavily on file-based locks (such as mail transfer agents qmail[5] and Postfix[6]) if the machine halts before it has synchronized the disk.[7]

and this:

> it is recommended not to store ReiserFS v3 images on a ReiserFS v3 partition (e.g. backups or disk images for emulators) without transforming them to a form that avoids misleading the file system, e.g., by compressing or encrypting

neither of which translates to anything like "breaks easily".

It also says:

> Compared to ext2 and ext3 in version 2.4 of the Linux kernel, when dealing with files under 4 KiB and with tail packing enabled, ReiserFS is often faster by a factor of 10&#8211;15. This is of great benefit in Usenet news spools, HTTP caches, mail delivery systems and other applications where performance with small files is critical.

which describes a whole lot of what the average Linux user spends his/her time doing, and also

> the current journaling implementation in ReiserFS is now on par with that of ext3's "ordered" journaling level.


So, I'm still looking for the "breaks easily" evidence ....  :(


Here's where someone actually did a decent job of testing Linux filesystems:

[http://linuxgazette.net/102/piszcz.html](http://linuxgazette.net/102/piszcz.html)


I wouldn't claim that there is a clear "best" filesystem, but rumors of unreliability in reiserfs are completely unfounded, as far as I can discover.  :)

---

### Post by Steveway on 2007-10-11
> **dabl said:**
> Huh? It doesn't say that ... doesn't say anything like that!  :confused:

It says this:



and this:



neither of which translates to anything like "breaks easily".

It also says:



which describes a whole lot of what the average Linux user spends his/her time doing, and also



So, I'm still looking for the "breaks easily" evidence ....  :(

Lol, you left out the point that said it:
> The tree rebuild process of ReiserFS's fsck has attracted much criticism: If the file system becomes so badly corrupt that its internal tree is unusable, performing a tree rebuild operation may further corrupt existing files or introduce new entries with unexpected contents [9]. But this action is not part of normal operation or a normal file system check and has to be explicitly initiated and confirmed by the administrator.

Nevertheless it is recommended not to store ReiserFS v3 images on a ReiserFS v3 partition (e.g. backups or disk images for emulators) without transforming them to a form that avoids misleading the file system, e.g., by compressing or encrypting. Reformatting an existing ReiserFS v3 partition can also leave behind data that could confuse the rebuild operation and make files from the old system reappear. This also allows malicious users to intentionally store files that will confuse the rebuilder. As the metadata is always in a consistent state after a file system check, corruption here means that contents of files are merged in unexpected ways with the contained file system's metadata. The ReiserFS successor, Reiser4, fixes this problem.

[edit] 

---

### Post by dabl on 2007-10-11
Well, yeah -- 

```
this action is not part of normal operation or a normal file system check and has to be explicitly initiated and confirmed by the administrator
```

I'm running 5 hard drives for a year on my system, through migration from Dapper to Edgy to Feisty to Gutsy, and I have never needed to do this operation -- it's a "nothing-burger".  Totally irrelevant to the daily operation of my system (and yours)!  :guitar:

---

### Post by dabl on 2007-10-11
More info -- hopefully a reliable source:

[http://www.debian-administration.org/articles/388](http://www.debian-administration.org/articles/388)

:)

---

### Post by Zill on 2007-10-11
I fell out with ext3 after power outages trashed my file systems a couple of times.  As a non-professional user I couldn't successfully rebuild the file system from the cryptic Linux CLI fsck commands so had to re-install everything.

I moved over to reiserfs two or three years ago and haven't looked back.  Totally reliable with no fsck or "lost and found" and the file systems have survived several power outages with no problems at all - it just works :-)

---

### Post by musther on 2007-10-11
Interesting, I just found this:

[http://linux.wordpress.com/2006/09/27/suse-102-ditching-reiserfs-as-it-default-fs/](http://linux.wordpress.com/2006/09/27/suse-102-ditching-reiserfs-as-it-default-fs/)

Some inside info from somebody involved with reiser and general OS development.

---

### Post by dabl on 2007-10-12
Now THAT'S informative --- Thanks!  :)

---

### Post by atlfalcons866 on 2007-10-16
read this

[http://linuxgazette.net/122/TWDT.html#piszcz](http://linuxgazette.net/122/TWDT.html#piszcz)

bench marks of the main filesystems

The future of there reiserfs is uncertain as hans reiser got arrested for the murder of his wife about 1 year ago

---

