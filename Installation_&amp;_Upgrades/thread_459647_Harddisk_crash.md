---
title: "Harddisk crash"
date: 2007-05-30
forum: Installation &amp; Upgrades
---

### Post by dakochan on 2007-05-30
Hi,

I have 2 harddisks, windows os has been installed in the first harddisk and the second is for linux os. I use the both harddisk since a few years ago.

A few days ago I tried to install Feisty Fawn on my second harddisk, and I was trying to re-partition the harddisk using Gparted that come with the Ubuntu DVD. I planned the partition successfully in Gparted and started the process. But when process reached 96%, it showed an error, I forgot what the error messsage is. So, I was trying to do re-partition again. But after I set all the partition plan the Gparted could not start the process at all. It happened for several times.
At the end my bios cannot recognise the harddisk anymore. Seems the harddisk is broken.

Now I'm puzzled. Can the Gparted break my harddisk ?


Thanks.

---

### Post by ryanVickers on 2007-05-30
I don't believe it can actually do physical damage to it, but it might be messed up pretty bad.  There's *ware in it that does stuff, and it might be destroyed (not the drive, just some simple embedded scripts and stuff).  I would take it to a repair place like (the manufacturer) actually and see if they can bring it back to life.  Another recommendation is (I love gparted, but) I wouldn't trust it to do more than 1 or 2 operations at a time!

Hope you didn't lose anything! :(

---

### Post by southernman on 2007-05-31
I was reading psychocats howto on backing up using Partimage. It mentioned [http://www.sysresccd.org/Main_Page]("http://www.sysresccd.org/Main_Page")... with a link. Needless to say, I followed the link and really liked what I read on this livecd. I believe they also boast about having software on the cd that can (sometimes) bring a HDD back from the brink of outspace.

I'd have a look, if'n I were you...

To answer your question: Like ryanVickers, I don't think it can actually destroy your hard drive.

Render it uselsss? It's happened to others. Not something that wasn't fixable though. Now, if your hard drive were in it's final stages, loading Gparted up with task at once may be the final shot to put it out of it's misery.

---

