---
title: "Is this a reasonable partition method?"
date: 2007-02-12
forum: Installation &amp; Upgrades
---

### Post by dryder on 2007-02-12
Hi,
Looking through very many posts - just a 'thank you' to all the volunteers helping us. 

I have found and used the installation method that is exactly what I was after. gn2 - thank you! [COLOR="Red"][http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)[/COLOR].

May I ask for experience please in folder/partition setup? I anticipate large use as I don't want to re-install often :) 

I have installed Ubuntu on my ide primary slave with these partitions (no interference with Windows MBR using the above method):
/[COLOR="White"]......[/COLOR]250MB primary set to B[oot] (without it I had an error message that it wouldn't be able to start the system even though /boot was set to B[oot])
/boot 5GB primary
/usr  10 GB primary
/home 20 GB logical
/var  10 GB logical
/tmp 5 GB logical
swap 1.5 GB
/opt  20 GB logical
/store 58GB approx logical

I realize some are large but I have no idea at this stage how much I need (being a wannabe ex-M$ user asap!)

One difficulty I am having is not seeing and therefore not being able to mount my XP data files - which I would very much like to move over (word, excel, movie files etc). I have yet to figure out how to search other drives on this computer. (I have not yet started to figure out networking!!) gulp:confused: 

Many thanks,
David

---

### Post by kerry_s on 2007-02-12
Since your just starting, i think you should keep it simple, just use 3 partions> root(/),swap(1gig is enough),/home <the sizes depends on your needs, applications get put in /(root) so if your going to install alot give some space(5gig minimum). What ever extra you have just use for your home, home is going to hold all your settings and personal files.

---

### Post by Kateikyoushi on 2007-02-13
I concur do not use more than 3 partitions if this is your first advanture in the linux realm.
I would make / a bit bigger since you might try different setups even might install kde and gnome smae time to find what is the best for you.

---

### Post by dcstar on 2007-02-13
> **Kateikyoushi said:**
> I concur do not use more than 3 partitions if this is your first advanture in the linux realm.
I would make / a bit bigger since you might try different setups even might install kde and gnome smae time to find what is the best for you.

Absolutely agree with the previous 2 posts - 5GB (minimum) for the root partition and make a separate /home partition if you like.

Splitting up all those other partitions just unnecessarily complicates things with little benefit.

---

### Post by dryder on 2007-02-13
Thank you all very much - I will keep / to 8GB, /swap - twice mem size I've seen in posts have always used the principle of 2x - I have 1GB RAM so 2 GBG? and /home 20GB for my data - doesn't seem much though if a movie file is 4.6GB and then I have a lot of documents and spreadsheets, etc.

I actually copied the setup from quite a few posts on partitioning and have an old Unix habit of keeping the OS separate from data separate from programs, etc.
 
If my programs go in / won't they be 'mixed up with' the system startup or OS files?

I just like things neat and in places where re-installing won't destroy data or downloaded applications I have kept. Updates could then simply be re-applied. And keeping downloaded applications so they could be installed after a system re-install.

Many thanks,
David :)

---

### Post by IgnorantGuru on 2007-02-13
You can see my partitioning suggestions here...
[http://www.ubuntuforums.org/showthread.php?p=2148017#post2148017](http://www.ubuntuforums.org/showthread.php?p=2148017#post2148017)

As for programs mixed with the OS, I never liked that about Windows, but linux manages it much better.  Most programs stay in their place, and when you remove them, they are completely removed.  So the OS and software sharing the partition seems to work well.  I think it would actually be more complicated if you tried to separate them, and I don't think it would accomplish much - programs that need to mess around with the system files are still going to do so.

Also, the line between 'software' and 'OS' gets blurred, especially in linux.  Aside from the kernel and drivers, the OS is just a collection of software, after all.

---

### Post by dryder on 2007-02-13
Hi IgnorantGuru,

Please don't let that link 'fade away' - is there a place it can be that is kept as a reference source on the net? :)

It is along the lines of exactly what I was trying to do (and am comfortable with). Not that I want to keep M$ in the medium/long term but that part has other uses too.

One of the frustrating things is I was used to Unix manuals - wikipaedias seem to sometimes conflict and not be as easy to refer to for things like the command structure, if you know what I mean ... but then, of course, you pay for those huge manuals !!!

Many thanks to all.

David

---

### Post by IgnorantGuru on 2007-02-13
> Please don't let that link 'fade away' - is there a place it can be that is kept as a reference source on the net?

I find a lot of answers in archived forums, so I figure it will show up in a search.  I suppose I could put it on a wiki - not sure where though.  (Anyone have a suggestion?)

I still have a windows partition, but I boot into it about once a year.  It always looks so strange (and blurry) now.  And my laptop came with a copy of windows, so I figured I would leave it on a partition on there.  But again, I rarely boot into it.  I just don't have any use for Windows anymore.  :)

---

