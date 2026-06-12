---
title: "New Hard Drive"
date: 2007-05-19
forum: Installation &amp; Upgrades
---

### Post by OmahaVike on 2007-05-19
Very doubtful that this may be answered, so all help is greatly appreciated....

Installed 6.06LT quite a while ago, and am now running out of space on my hard drive.  So, I went out and bought a new sata 400g.  Ubuntu recognizes the drive, and I've formatted it to ext3.  I know (thankfully to this forum) how to mount it on it's own root directory, so no problem there.

The question I'm hoping others may have an answer to is...   How can I allocate all of the new 400g across the root directory?

In other words, I can install a new HD and mount it to "/newhd", but only that specific directory tree will have the extra allocated space.  But I don't want that, I'm seeking to spread the new 400g (aka, spread the love) across the entire root "/" filesystem.

Thank you in advance for all the help you may lend.

---

### Post by spin2cool on 2007-05-19
There's no easy way to do that, and you probably wouldn't want to.  It's a good idea to keep your data partitions and your OS partitions seperate.  That way, if you hose your installation, decide to reinstall from scratch, or decide to abandon Ubuntu in favor of something else, you don't have to worry about your data.  It's safely on your other partition.  (often people just move their entire home folder to this other partition/drive)

It's pretty difficult to fill a root filesystem with more than 10-15 gigs, as long as your data is seperate.  Right now, my root partition is sitting at 4 GB out of 15, and I have everything I need installed and then some.

---

### Post by OmahaVike on 2007-05-19
makes sense.  thanks for straightening me out.

---

### Post by tormentum on 2007-05-20
spin2cool is right.  I tend to set my partitions up like this:

sda1: /    (15gb)
sda2: /home (rest of capacity)
sda5: swap (size of RAM x 2)

This way when you reinstall ubuntu later on, all your files in the /home partition are untouched when you format the / (root) partition.  It's worth wiping the current disk and setting it up properly the first time mate, as it makes things MUCH easier later on when you start upgrading ubuntu installations etc

---

