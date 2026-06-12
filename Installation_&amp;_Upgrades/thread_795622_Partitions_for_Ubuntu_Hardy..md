---
title: "Partitions for Ubuntu Hardy."
date: 2008-05-15
forum: Installation &amp; Upgrades
---

### Post by glore2002 on 2008-05-15
Hello! :)

Since I am planning to re-install Ubuntu Hardy and use it as my primary OS, I want to make sure I install the system properly from the beginning.

Since there are many (maybe too many) and different opinions about partitioning, I would like to share two schemes and, with your help, define which one is OK for me or what kind of modifications I should make to them in order to improve system performance.

My hard disk: 160 Gb (SATA II). RAM memory: 4Gb

Scheme 1:
        a) /
	b) /home
	c) /usr/local
	d) SWAP

Scheme 2:
        a) / 
	b) /home
	c) SWAP

/ is needed because system files will go there.

As far as I know, creating a separate partition for /home is better because if I need to reinstall the system, I won't lose my documents. 

In scheme #1, /usr/local partition should be for compiled software. 

I think Scheme #2 is good enough but I found scheme #1 in a Slackware book and it also looks interesting. 

SWAP partition is another point. There are many recommendations. One I like says SWAP should be (when more than 2Gb RAM) memory size + 2. This in order to suspend the system without problems, etc. So, in my case, I would create a 6Gb SWAP partition.

My doubts are:
a) What scheme and What size would you suggest for the partitions?
b) Which partitions should I create as Primary and which ones as Extended (logical)?
c) Is it important the order (from left to right) in which I create the partitions or not?
c) Any recommendation will be really appreciated.

Thanks in advance for your help,
Glore2002.-

---

### Post by mikewhatever on 2008-05-15
It looks like any of the schemes would do, but you surely don't need 6 GB of swap. In fact, there is no way 2 GB +2 can equal 6. I think about 2 GB is more then enough for swap, since most of it would be used for suspension  to disk.

---

### Post by damis648 on 2008-05-15
If I were you, I would not (and do not) use a /home partition. Its better this way because you don't have to worry about running out of space. In that situation, I would do the following:

4 gb SWAP
156 gb /

---

### Post by glore2002 on 2008-05-16
> **mikewhatever said:**
> It looks like any of the schemes would do, but you surely don't need 6 GB of swap. In fact, there is no way 2 GB +2 can equal 6. I think about 2 GB is more then enough for swap, since most of it would be used for suspension  to disk.

I have 4Gb RAM memory. That's why memory+2 equals 6. How can I know how much swap is needed for suspension? 

Thanks for your help!

---

### Post by glore2002 on 2008-05-16
> **damis648 said:**
> If I were you, I would not (and do not) use a /home partition. Its better this way because you don't have to worry about running out of space. In that situation, I would do the following:

4 gb SWAP
156 gb /

I understand what you say and this is, in fact, the scheme I'm using right now (dual boot with windows) but: What would happen if I need to reinstall the system? On the other side, if using separate partitions, Which one should be bigger / or /home?
Regarding to SWAP, I have 4Gb RAM. Would 4Gb SWAP be enough for suspension?

Thanks again for your valuable help!

---

### Post by damis648 on 2008-05-16
Were the /home and / be different partitions, /home should be much bigger. If they are one single partition, you would have to just back up the /home in order to reinstall, because the is the same partition.

---

### Post by Cato2 on 2008-05-16
Here's what I've done on a new install:

/ - 30 GB
/data - 20 GB - for music, data and /home
   - includes /data/home, with /home symbolic link to /data/home
/extra - 10 GB - for /usr/local and /opt
   - symlinks from /opt and /usr/local to directories under /extra
Swap - 4GB - same as RAM, primarily for use when hibernating

If you want to simplify this, you could put everything under /data, i.e. /usr/local and /opt are symlinked to directories under there.  

Example of symbolic linking:```
sudo bash
cd /usr
rsync -avH local /extra
mv local local.junk
ln -s /extra/local /usr/local
```

The rsync command copies everything, preserving permissions through -a and hard links through -H (as long as they are within the /usr/local hierarchy - any hard links outside the hierarchy must be manually symlinked.)  Rsync is much better for this purpose than 'cp -pr' and simpler than using two tar commands and a pipe.  When you are happy this has all worked you can remove the old /usr/local.junk tree.

Symbolic links are very handy here.  The end result is that you can clean install as much as you like, and just re-do the symbolic links as needed (saving this as a shell script under your home dir might be a good idea).  When clean installing you only need to save any changed files under /root and /etc, typically.

One other thing to think about is LVM - this lets you dynamically expand filesystems by putting all storage into one large 'volume group', so it's much less important to get the sizes exactly right up front.  Ubuntu supports this but not perfectly - some command line work is unavoidable, so if you don't want that then just use normal partitions.

---

### Post by glore2002 on 2008-05-16
> **Cato2 said:**
> Here's what I've done on a new install:

/ - 30 GB
/data - 20 GB - for music, data and /home
   - includes /data/home, with /home symbolic link to /data/home
/extra - 10 GB - for /usr/local and /opt
   - symlinks from /opt and /usr/local to directories under /extra
Swap - 4GB - same as RAM, primarily for use when hibernating

If you want to simplify this, you could put everything under /data, i.e. /usr/local and /opt are symlinked to directories under there.  

Example of symbolic linking:```
sudo bash
cd /usr
rsync -avH local /extra
mv local local.junk
ln -s /extra/local /usr/local
```

The rsync command copies everything, preserving permissions through -a and hard links through -H (as long as they are within the /usr/local hierarchy - any hard links outside the hierarchy must be manually symlinked.)  Rsync is much better for this purpose than 'cp -pr' and simpler than using two tar commands and a pipe.  When you are happy this has all worked you can remove the old /usr/local.junk tree.

Symbolic links are very handy here.  The end result is that you can clean install as much as you like, and just re-do the symbolic links as needed (saving this as a shell script under your home dir might be a good idea).  When clean installing you only need to save any changed files under /root and /etc, typically.

One other thing to think about is LVM - this lets you dynamically expand filesystems by putting all storage into one large 'volume group', so it's much less important to get the sizes exactly right up front.  Ubuntu supports this but not perfectly - some command line work is unavoidable, so if you don't want that then just use normal partitions.

Thank you! Very interesting explanation.
Glore2002.-

---

