---
title: "Reinstalling Ubuntu over Linux Mint"
date: 2012-01-19
forum: Installation &amp; Upgrades
---

### Post by kvalenza on 2012-01-19
I have a dual boot of Windows 7 and Linux Mint. I would like to install Ubuntu 11.10 in the Mint partition, thus eliminating Linux Mint.  I do not want to keep Mint.

What steps do I need to take in order to do this when I install Ubuntu from the CD?

---

### Post by mips on 2012-01-19
Just select manual partitioning and select the mint partition(s) to use.

---

### Post by kvalenza on 2012-01-19
I know that much....but HOW do I do that? I know there are specific steps I need to take, but I don't know what those steps are. Please tell me, step by step, how to do that so that I do it correctly.

---

### Post by nothingspecial on 2012-01-19
Back up data

Boot live cd

Start installer

Choose "something else" when asked how you want to install Ubuntu

Select Mint partition (it will be ext4, windows will be ntfs) and right click to edit it.

Choose to format it.

Choose to use it as an ext4 journaling file system.

Choose a mountpoint of /

**[COLOR="Red"]Do not touch the ntfs partition[/COLOR]**

That's it.

---

### Post by BlinkinCat on 2012-01-19
If you posted the result of Gparted here, others may be able to guide you more simply.

Edit: My suggestion not needed - Thanks nothingspecial - :)

---

