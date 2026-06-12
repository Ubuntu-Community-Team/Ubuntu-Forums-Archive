---
title: "Help changing from wubi to just ubuntu"
date: 2012-08-01
forum: Installation &amp; Upgrades
---

### Post by Moesephur on 2012-08-01
Hello Everyone:
This is my first post. Yay!. Ok now that that's over. I'm new to ubuntu and linux in general. Last night I downloaded Wubi (windows installer) and for the life of me didn't realize that it would be a dual boot and not just ubuntu. I've looked through the ubuntu on the netbook (gateway LT21) to figure out how to get rid of windows, but I'm just not seeing it. Will I have to just uninstall wubi and redo the whole process or is there another way?

---

### Post by Mark Phelps on 2012-08-01
By far the easiest way, if you just want Ubuntu, is to boot from the install CD and select the option to use the entire drive.  That will erase the drive and repartition it.

There is a way to "move" a Wubi installation to a separate partition, but it's very involved and only worth the effort if you need to retain dual boot with Windows (section 8.8):

[https://wiki.ubuntu.com/WubiGuide]("https://wiki.ubuntu.com/WubiGuide")

---

### Post by bcbc on 2012-08-01
There is a way to [move]("https://help.ubuntu.com/community/MigrateWubi") a wubi install to a normal install, but it doesn't get rid of windows, and in your case you have a fresh install so it would be easier to do a fresh install.

---

### Post by bcbc on 2012-08-01
> **Mark Phelps said:**
> There is a way to "move" a Wubi installation to a separate partition, but it's very involved 
I've seen that mentioned fairly frequently. I'm not sure why people say it's involved. This is the process to migrate:
1. Create the target partition(s)
2. Download a script
3. Run the script

In my mind that's no more complicated than creating a live CD/USB and running the Ubuntu installer (with manual partitioning). If you also need to backup and restore data and settings then I'd say that this is 'more involved' than migrating.

This probably isn't the right place to have a debate about it, I welcome all feedback in [this thread]("http://ubuntuforums.org/showthread.php?t=2012400") and I'll try to make it simpler. Thanks

---

### Post by Moesephur on 2012-08-02
Thank you both. I decided to just delete Wubi through windows and make a thumb drive. It worked. I'm so excited to start working with Ubuntu and to learn all I can. Right off the bat it seems very different than what I'm used to. Feel like a 1st grader again.

---

