---
title: "Hosed Ubuntu on upgrade: reinstall without formatting?"
date: 2006-07-23
forum: Installation &amp; Upgrades
---

### Post by diamond on 2006-07-23
I followed the instructions to upgrade from Breezy to Dapper with apt, and something got screwed up. I am now unable to log into Ubuntu.

I'm not too freaked out by this; I'm willing to just do a fresh install from the Dapper CD. It will be a bit of a pain having to reinstall all of the packages I had before, but I can handle that. The only files that are truly irreplaceable (code I've written, pictures, etc.) are all contained under my home directory. However, that directory is about 2.5GB in size, so backing it up will be a real pain.

My question is this: can I do a fresh, from-scratch installation on an existing Linux partition without having to reformat? If I tell it to install to an existing partition, will it overwrite all files and directories there, including "/home", or will it leave my home directory alone? Or, alternatively, if I boot from the liveCD and copy my home directory to another path on the same partition (one that isn't part of the standard Linux install, like "/home-backup"), then run the install, will the installer leave that directory alone?

---

### Post by aysiu on 2006-07-23
[http://www.psychocats.net/ubuntu/separatehome.html](http://www.psychocats.net/ubuntu/separatehome.html) may help you, but you need a live CD for that.

By the way, can you elaborate a bit more on "now unable to log into Ubuntu"? What happens? Have you tried both a graphical and terminal login? Can you boot into recovery mode?

---

### Post by diamond on 2006-07-23
> **aysiu said:**
> [http://www.psychocats.net/ubuntu/separatehome.html](http://www.psychocats.net/ubuntu/separatehome.html) may help you, but you need a live CD for that.

So installing Ubuntu will completely wipe the existing partition?

> By the way, can you elaborate a bit more on "now unable to log into Ubuntu"? What happens? Have you tried both a graphical and terminal login? Can you boot into recovery mode?

It gets me to the login screen, but when I log in it just dumps me back out again. I can log in with a basic terminal, and I *might* be able to figure out the problem from there, but I think it would be easier to just do a fresh install.

---

### Post by aysiu on 2006-07-23
> **diamond said:**
> So installing Ubuntu will completely wipe the existing partition? Yes, unless you have a separate /home partition.

Do you have a live CD?

---

### Post by Sef on 2006-07-23
> So installing Ubuntu will completely wipe the existing partition?

Yes.  it will be completely wiped out.  However, if you have a separate home partition, it won't be wiped out as long as you don't repartition it.

---

### Post by diamond on 2006-07-23
> **aysiu said:**
> Yes, unless you have a separate /home partition.

Do you have a live CD?

I have the Dapper live/install CD. I also have a working WinXP partition, so I can download and burn any other Live CD.

The problem I see with creating a separate /home partition is that the size of that partition is fixed, even after I re-install Ubuntu. I just don't know how much space I might need for it in the future.

Here's an idea: If I can figure out a way to burn CDs from the command line, I can just copy the contents of the home directory onto several CDs. Are there any command-line CD burning utilities that I might be able to use (preferably already installed by default with Ubuntu)?

---

### Post by aysiu on 2006-07-23
I don't know of any command-line burning utilities (I'm sure there are many--I just don't know what they are), but if you have a live CD, you can easily burn from there.

Or you can also copy the files over to your Windows XP partition using this: [http://www.fs-driver.org](http://www.fs-driver.org)

---

### Post by diamond on 2006-07-23
> **aysiu said:**
> I don't know of any command-line burning utilities (I'm sure there are many--I just don't know what they are), but if you have a live CD, you can easily burn from there.

Or you can also copy the files over to your Windows XP partition using this: [http://www.fs-driver.org](http://www.fs-driver.org)

Slick. That'll take care of it..

Thank you very much.

---

