---
title: "Installation Preparation"
date: 2006-06-04
forum: Installation &amp; Upgrades
---

### Post by Cable on 2006-06-04
Well, I think I'm going to be setting up a dual boot with Ubuntu and Win XP Pro...still need XP for games unfortunately.  Anyway, I have some questions.

1)  Mount points...are these basically just what directory a drive or partition shows up under in the file manager?

2)  When installing apps (packages I guess they're called, correct?)  Are they all installed to a default place?  In Win XP, I have my partitions kind of organized.  I have separate partitions for games, applications, music, the OS itself, and then just my other stuff.  Any need to do that in Ubuntu?  If so, how do I configure where apps are installed and stuff?  Tell me if this is unnecessary for whatever reason...

3)  I'll need to be able to read *and* write to my music partition, and also to my two stuff partitions.  I read that Linux can only read NTFS, and all of my partitions are, in fact, NTFS.  I did find the Ext3 driver for Win XP [here]("http://www.fs-driver.org/").  Would that be my best choice?  I'm just trying to figure out the best way to do this.  What I'm thinking at the moment is copy all of my music to a different hard drive (removable or something), change that partition to Ext3, then move everything back.  Then, do the same thing with both of the other partitions.  Seems like it would be a pain, but if that's what I have to do then I'll do it.  Any other suggestions are welcome.

4)  I had another question...can't think of what it was at the moment...

---

### Post by aysiu on 2006-06-04
I hope this link helps to answer at least some of your questions:
[http://www.psychocats.net/ubuntu/partitioning.html](http://www.psychocats.net/ubuntu/partitioning.html)

and this link also:
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)

---

### Post by Cable on 2006-06-04
I just remembered the question I couldn't think of...is there a maximum size for Ext3 partitions?  I have 2 250 GB drives and have rather large partitions in NTFS.

---

### Post by aysiu on 2006-06-04
[QUOTE=Cable]I just remembered the question I couldn't think of...is there a maximum size for Ext3 partitions?  I have 2 250 GB drives and have rather large partitions in NTFS.[/QUOTE] There's no maximum size that I know of.

---

### Post by Cable on 2006-06-04
Ok, so from what I understand in reading those links, apps are installed in the /home directory, and there's not a way to change that.   Also, I can create as many other partitions as I want, and when configuring the size, et cetera of the partition, I can specify the mount point (i.e. Music or Stuff).  Am I correct?

Any suggestions for question 3 in my first post?

---

### Post by aysiu on 2006-06-04
[QUOTE=Cable]Ok, so from what I understand in reading those links, apps are installed in the /home directory, and there's not a way to change that.   Also, I can create as many other partitions as I want, and when configuring the size, et cetera of the partition, I can specify the mount point (i.e. Music or Stuff).  Am I correct?[/QUOTE] Actually, apps are installed outside the /home directory--usually in /usr and /lib, among other places. For repositories applications, it doesn't really matter *where* the application is installed--the launcher will usually be the name of the application.

I have no idea where Epiphany installed to, but if I click the Epiphany Web Browser launcher icon, it launches Epiphany. If I type ```
epiphany
``` in the terminal, it launches Epiphany.

You don't need to have a separate partition for music or other stuff--all your files will go within your /home/cable folder. Creating a separate /home partition is just advantageous for keeping your settings and files intact should you wish to reinstall Ubuntu or do a clean reinstall of a newer version of Ubuntu (say, Edgy Eft in six months).

> Any suggestions for question 3 in my first post? Yes, I would suggest Ext3 and the [http://www.fs-driver.org](http://www.fs-driver.org) driver for Windows.

---

### Post by Cable on 2006-06-04
Ok, thanks.  I think I'll be going with having a separate /home partition just to be safe, and also have a separate /Music and /Stuff partition just because I like to keep things organized and easy to find like that.  I'm just sort of picky.  :-P

What's a good size for the OS partition?  I'll use a 2 GB swap since I have 1 GB of RAM (I read that the swap should be at least twice the size of your RAM).

---

### Post by aysiu on 2006-06-04
Before you get started I would suggest playing around with the Ubuntu live CD for a week or two:

1. It'll give you a sense of how well Ubuntu detects your hardware
2. It'll familiarize you with the interface before you have to troubleshoot problems (if you do have to)
3. You can see whether Ubuntu is something you really want or not before committing to an actual installation

Once you're sure you want to install Ubuntu, read both of these links all the way through. It's always better to ask questions *before* you do something permanent.

[http://www.psychocats.net/ubuntu/windowstoubuntu.html](http://www.psychocats.net/ubuntu/windowstoubuntu.html)
[http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone)

Oh, and **back up all your data**.

---

### Post by Cable on 2006-06-04
Oh yes, I will most definitely back up all of my important stuff!

---

