---
title: "Reinstalling Ubuntu - /home partition?"
date: 2006-10-26
forum: Installation &amp; Upgrades
---

### Post by me1on on 2006-10-26
Now that Edgy's out, I've decided to reinstall Ubuntu. I don't have a separate /home partition, and now that I'm seeing how useful having one would be, I'd like to make one when I reinstall Ubuntu. :)

I'm not exactly sure how I'd make a home partition or what size I should make it. Here are my current partitions:

/dev/hda1 (windows recovery partition) - 4.5 GB
/dev/hda2 (windows partition) - 30 GB
/dev/hda3 (ubuntu partition) - 21 GB
/dev/hda5 (swap partition) - 1 GB

Should I just make the ubuntu partition smaller then create a /home partition out of the remaining size? How big should the /home partition be?

---

### Post by woedend on 2006-10-26
it depends on what you do with it and where you put your personal media/document files.  If you just want settings and a few things saved, something as small as even 1 or 2 gig would be fine, although id make it 5 just in case you get into downloading a big DVD ISO or something.  If you plan to store your files/documents there, you could try a 8-13 split(13 for home).  It depends on what you install and whatnot...it really is a personal preference and how you use it.  How much room are you currently using in your ubuntu partition?  What I do typically is make an unnamed ext3 partition thats about 70% of free space, then use 30% for the base(root) partition.  I keep all of my files on the 70% time, and if, say, I wanted to keep all of my settings, id copy my home folder to said partition, reinstall, then move it back.

---

### Post by me1on on 2006-10-26
Thanks, that was very helpful. Right now I'm only using 12 gigs on my ubuntu partition, with the /home folder having ~5 gigs. I'll probably make my /home partition use 12 GBs and my other partition use 9 GBs.

---

