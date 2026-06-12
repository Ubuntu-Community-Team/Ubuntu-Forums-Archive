---
title: "Problems with EasyTag"
date: 2010-02-19
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by darkhole on 2010-02-19
I'm using Ubuntu 10.04 with last updates, and I want to change some ID3 tags from my music, but, when I open EasyTag and choose a folder with music files, EasyTag keep looking for songs, but, for example, I try this with a folder of just 10 songs.

By the way, the CPU climbs up in this process.

This happen to you? Can you test it?

---

### Post by ajgreeny on 2010-02-19
In the Easytag settings Preferences, remove the tick from "Search subdirectories" but leave it in "Show subdirectories".  That may help out.  I think I had the same problem in karmic until I did that.

If that is not successful, have a look at tagtool as an alternative application; not as good in some ways, but still useful for the odd music file.

---

### Post by darkhole on 2010-02-19
This is not the problem, I can wait some seconds, but, I'm talking about a problem, and, to have arguments I use your suggestion with the same problem.

I had been using Ubuntu since a lot of time, and also EasyTag (from 8.04). And this is the first time that I have this problem with EasyTag, on Ubuntu 10.04 Lucid Lynx.

can you test EasyTag on Lucid Lynx?

---

### Post by portis on 2010-02-19
I have the same problem.
I also tried to import a folder into rhythmbox, and had the exact problem of easytag.


> **darkhole said:**
> This is not the problem, I can wait some seconds, but, I'm talking about a problem, and, to have arguments I use your suggestion with the same problem.

I had been using Ubuntu since a lot of time, and also EasyTag (from 8.04). And this is the first time that I have this problem with EasyTag, on Ubuntu 10.04 Lucid Lynx.

can you test EasyTag on Lucid Lynx?

---

### Post by darkhole on 2010-02-19
OK!! We found a bug!!! I have the same behavior in Rhythmbox. So, this is not EasyTag+/Rhythmbox roblem.. Mmm, we need some help from devs or testers.. maybe is a GTK issue?

---

### Post by portis on 2010-02-19
I've no idea.
I can import mp3 files into banshee.

> **darkhole said:**
> OK!! We found a bug!!! I have the same behavior in Rhythmbox. So, this is not EasyTag+/Rhythmbox roblem.. Mmm, we need some help from devs or testers.. maybe is a GTK issue?

---

### Post by darkhole on 2010-02-19
Becomes more tricky, I just reboot Ubuntu and Rhytmbox is working fine.. but EasyTag still have the same problem.

---

### Post by portis on 2010-02-23
It's a gtk bug, and has been fixed.

gtk+2.0 (2.19.5-1ubuntu5) lucid; urgency=low

  * debian/patches/062_client_side_decoration.patch:
    - update by Cody Russell to really fix excessive cpu usage issues
      (lp: #523949, #524304)

---

### Post by darkhole on 2010-02-23
Yes, I test it :) Thanks!!
[https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/524304](https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/524304)
[https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/523949](https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/523949)

Solved for me.

---

