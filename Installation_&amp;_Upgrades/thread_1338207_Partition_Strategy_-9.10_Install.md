---
title: "Partition Strategy -9.10 Install"
date: 2009-11-26
forum: Installation &amp; Upgrades
---

### Post by jv2112 on 2009-11-26
I am planning on installing 9.10 on a Terabyte drive but want to keep "Home" separate on a different partition so I can experiment with different distros. However I am a novice and I never seem to get the manual partition correct. 

Assuming with your advice I get it correct. How do I install a new distro later without nuking the "Home" partition.

All Guidance is Appreciated!!!!!!! 

Thank You!!!

---

### Post by Bartender on 2009-11-26
Installing a new distro without runining an existing /home is relatively simple.

#1.  You have to go into the "Manual" partitioning mode.
#2.  Make sure to mount the existing /home partition as /home.
#3.  At this same step, make sure to leave the "Format" box unchecked.  Repeat: do NOT format the /home folder.
#3.  Use the same username/password as the previous install.  

I made the mistake once of using a different username during installation and ended up with a new /home inside the / partition.  That was in addition to the previous /home!  The new /home was identified with the new username, and the old /home retained the previous username.

---

### Post by audiomick on 2009-11-26
Bartender's advice is good if you already have a /home partition you want to re-use.

If you are starting from scratch, as I think you are, try reading through this:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
first.
It starts off with "if you are running Windows", but even if you aren't, the links further down should tell you all you need to know.

this thread has also got a lot of good advice:
[http://ubuntuforums.org/showthread.php?t=1321649](http://ubuntuforums.org/showthread.php?t=1321649)

The general opinion about appropriate sizing is something like this:

/   between 10 and 15 GB. Mine has got about 6GB in it. 15 should give you enough elbow room for the next few years.

Swap   a bit bigger than your RAM. If it is smaller, the suspend and hibernate functions can't work

/home  the rest, 

or, /home as big as you think you need, and another data or backup partition on the rest, if you feel like it.

---

### Post by raymondh on 2009-11-26
> **jv2112 said:**
> want to keep "Home" separate on a different partition so I can experiment with different distros.



Bartender explained it well .... how to keep an existing /home.

When you do experiment with other distros, do you plan to use your existing /home to accommodate the distros' /home requirements?  Remember that different distros may have different config files/settings and that might cause conflicts.  Have a read at bodhi.zazen's guide ..

[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

because it did happen to me (config conflicts).

It's better to have a  /data in this case.  Or, if it is just an experiment ... dedicate your 1TB to your 'production' OS (root, swap, /home, data -if you are 2-boot) and just virtualize the distro curiosity ;)

Regards,

---

### Post by jv2112 on 2009-11-26
How do I set up ?

Root

Boot 

Swap

Anything Else 

What % of drive space should I set for each ?

Thanks Again !!!!!!

---

### Post by Bartender on 2009-11-26
Oh, hey, sorry jv -
My advice was geared towards installing a newer version of Ubuntu over the old.  I'm pretty sure the advice still holds for other distros.  If you choose to multi-boot I think you'll find  that things will get more complicated really quickly.

A few years back, when I'd first found out about Ubuntu, I decided I wanted to try several different distros in a multi-boot scheme.  It seemed really cool and geeky, and after years of MS's control over my choice of OS the idea of multi-booting felt like giving MS the big ol' one finger salute.

It was confusing, but I persevered.  Then the first time I got a kernel update the whole thing went off the tracks.  I learned about UUID but decided it wasn't worth the hassle.  My brain could only handle so much new knowledge and it made sense to focus on one distro rather than flailing away at three.

If you have access to a handful of old HDD's it might be much easier to install one or two OS'es to each one and physically swap them around, rather than try to maintain a multi-boot scheme.  While multi-booting can get messy, dual-booting on one drive is pretty simple.  If you had two drives you could play with four OS'es.

Just sayin'

---

### Post by audiomick on 2009-11-26
> **jv2112 said:**
> How do I set up ?

Root

Boot 

Swap

Anything Else 

What % of drive space should I set for each ?

Thanks Again !!!!!!

Rule of thumb as I listed in #3. Read the thread I linked to. It is long, but it will give you a very good insight into this question.

---

### Post by Alex Libman on 2009-11-26
Unless you're using some really exotic partition types, you can usually get by without a separate /boot partition by installing boot loader (ex. [GURB]("http://en.wikipedia.org/wiki/GNU_GRUB")) on [MBR]("http://en.wikipedia.org/wiki/Master_boot_record") and keeping a rescue CD (ex. [Parted Magic]("http://partedmagic.com/")) nearby in case you need it.

No one needs more than at very most 2-3 gigs swap space on a desktop, and if you're short on space you can make do without a swap partition by [creating a temporary swap file]("http://www.cyberciti.biz/faq/linux-add-a-swap-file-howto/") on an existing partition if/when you need it, and removing it when you don't.

Also it is very rare for you to need more than 5-10 gigs for a desktop Linux partition - if you need more you're probably storing a lot of files (ex. huge game data-files, clip-art, [public_html]("http://httpd.apache.org/docs/2.0/howto/public_html.html"), etc) that would be better stored on your /home partition, so you could access them under different distro's.  You can always create a dummy /home/shared user folder that all other users can access.  You might also want to make sure programs like your BitTorrent client are storing temp / unfinished files on your /home partition as well.

So you'd usually want to create a ~10 gig partition for your main OS, then a couple smaller partitions for experimental distros (with Windows partitions, if any, going on the front of the drive), then the rest of your drive for a large shared /home partition, and finally a couple gigs for permanent swap (if any).  In dedicated server situations it sometimes makes sense to store other parts of the [filesystem hierarchy]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard") on different partitions, but for home desktop / developer setup it does not.

And a last piece of advice - if you have a pretty fast system, it might be better to try new distros in [VirtualBox]("http://en.wikipedia.org/wiki/VirtualBox") / [QEMU]("http://en.wikipedia.org/wiki/QEMU"), because most of the time you'll go "meh, nothing special here" and be done playing with it after a day or two.  This especially applies to Solaris / *BSD / MINIX, which might be a bit more tricky to partition, which means a greater chance of something going wrong.

The only time I find having a second Linux root partition useful is for [Gentoo]("http://en.wikipedia.org/wiki/Gentoo_Linux") - you can chroot to your Gentoo partition to [-O3 everything]("http://funroll-loops.info/") in the background while enjoying Ubuntu in the foreground.  \\:D/

---

### Post by raymondh on 2009-11-26
Nice to have all the space (1TB) ;)

Single or dual/multi boot?

If dual boot, ensure that your BIOS is capable of booting beyond 136gb or you risk an ERROR 18 on the 2nd OS you install.  Most recent vintage systems are able to.  Early 2000 vintage still have the 136GB limit.  If single boot, no problem then.

Are you planning to partition the other distros or virtualize?

Assume you decide to partition and you decide you need a /boot :

* Linux and Ubuntu (and most distros') don't care if it reside in a logical partition.  My suggestion is to create an extended partition which can then house the various distros in logical partitions.

/boot - 1GB is way plenty (but then again, you have all the space 'eh).  No less than 200mb should be OK.
root (for each distro) - 8 to 10GB
/home (for each distro) - 10-15GB mounting each /home to their respective root as I believe this is better than 'sharing /home amongst distros.
Swap - about 2GB should be enough

*  The data partition can be a primary partition and in NTFS format

* remember to LABEL them accordingly so your future work/re-do would be easier to identify.

This can complicate this easily given that it is an experiment.  Should you decide to simplify and just virtualize your curiosities .....

Windows - 50GB is ok / primary
Swap 2GB as logical inside an extended
Ubuntu root - 8-10GB / Logical inside and extended
Ubuntu /home - 20-50 GB / logical inside an extended.  The sizing is thinking about the virtualized space for those other distros and just in case you decide to take space later on from here to make a true partition for another distro.
Data - primary / all remaining space.  You can also take space from here later on.

whew.

---

### Post by jv2112 on 2009-11-27
Thanks for all the guidance !!!!!!

Now that I have some clearer understanding I just need to pull it all together.

It is going to be 100% 9.10 (2.4 Ultimate Edition Variation) 

My goals is to utilize the quickest filesystem  and drive for the OS (fatstest) w/ Designated Storage (Home)(Next Fastest) /Sepeartate Partition & Back Up Seperate Partition.(Slowest)


I have-

Seagate Baracuda - 250 G  7200 RMP / 8 MB Cache

Samsung Spinpoint F1 750 G 7200 RPM  /32 Meg Cache

Seagate Baracuda - 1.5 Terrabyte /7200 RPM  /32 Meg Cache (Black Friday Rocks-$99...):D

I have just south of 1 terrabyte of data to store (alot of media)


Any thoughts / Suggestions ?

---

### Post by raymondh on 2009-11-27
> **jv2112 said:**
> 

My goals is to utilize the quickest filesystem  and drive for the OS (fatstest) w/ Designated Storage (Home)(Next Fastest) /Sepeartate Partition & Back Up Seperate Partition.(Slowest)


I have-

Seagate Baracuda - 250 G  7200 RMP / 8 MB Cache

Samsung Spinpoint F1 750 G 7200 RPM  /32 Meg Cache

Seagate Baracuda - 1.5 Terrabyte /7200 RPM  /32 Meg Cache (Black Friday Rocks-$99...):D

I have just south of 1 terrabyte of data to store (alot of media)


Any thoughts / Suggestions ?

250gb for root, /home of 9.10 and swap.  All as logical partitions iside an extended.  Say 4GB for swap .... 25gb for root ... rest for /home

750GB for data/media

1.5TB as back-up or files, image and extra storage for the remaining media (those that you could classify as "I-don't-need-to-access-always".

You could have the 1.5TB as your storage but you might run out of space when you try to back-up the media to the 750GB.

Regards,

---

