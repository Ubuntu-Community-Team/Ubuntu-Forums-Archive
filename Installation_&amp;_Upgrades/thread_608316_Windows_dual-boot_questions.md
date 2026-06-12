---
title: "Windows dual-boot questions"
date: 2007-11-09
forum: Installation &amp; Upgrades
---

### Post by RamFel on 2007-11-09
I tried Linux (I booted right from the CD) and I like what I see. 

But I have a question,

I have a Windows XP operating system (XP Pro) and want to do a dual-boot, but my hard drive is not partitioned. In other words, the entire hard drive is one partition.

So I want to buy a second hard drive and put Linux on it.

Will Linux handle the set up of the dual boot?
Do I need to do anything with Windows (like configure it in any way)?
My file system on my drive C is NTFS. Is this OK?

Is there a set of step-by-step instructions, or will Linux guide me through everything?

---

### Post by Craigus on 2007-11-09
You don't have to buy another drive, if there is free space on your existing one, but you can of course do it that way as well. You could have a look at wubi:

[http://wubi.sourceforge.net/]("http://wubi.sourceforge.net/")

This is a very safe way to go, and will work fine.

---

### Post by Harpoon on 2007-11-10
I just got a phone call and have to  run, but:
Yes, linux can be installed on a second hardrive and dual boot with windows, no problem;
You don't have to mess with windows at all to make it work;
NTFS will not be a problem for linux.

Also, you can avoid getting a second drive if you have space left on the one you have.  Second drives are noce to have, though.

I would prefer not using wubi in case you decide to keep ubuntu permanently.  It runs inside windows, and your installation will be lost if you delete/reinstall windows (I think that is correct??).

Cant't get to the links for you right now, but take some time to read a bit about partitioning for ubuntu.  It really is a good idea to have a separate /home directory, for example.  

I'm sure others will jump in to help you some more, but I must run.

Have fun!

---

### Post by Articfox3 on 2007-11-10
> **Craigus said:**
> You don't have to buy another drive, if there is free space on your existing one, but you can of course do it that way as well. You could have a look at wubi:

[http://wubi.sourceforge.net/]("http://wubi.sourceforge.net/")

This is a very safe way to go, and will work fine.

Cool Thanks you!
lol now I only have 20GB left for Windows Vista lol
I put it on my laptop

---

### Post by Craigus on 2007-11-10
> I would prefer not using wubi in case you decide to keep ubuntu permanently. It runs inside windows, and your installation will be lost if you delete/reinstall windows (I think that is correct??).

True, however you can migrate your wubi install to its own partition later using LVPM:

[http://lubi.sourceforge.net/lvpm.html]("http://lubi.sourceforge.net/lvpm.html")

---

