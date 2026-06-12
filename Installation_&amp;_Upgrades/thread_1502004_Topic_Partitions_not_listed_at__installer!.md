---
title: "Topic: Partitions not listed at  installer!"
date: 2010-06-05
forum: Installation &amp; Upgrades
---

### Post by srikar on 2010-06-05
I have windows installed in c drive and there are 3 other partitions namely e,d,f.I booted kubuntu/ubuntu live cd.The installer doesnt show any partitions.

This is my windows:-
[http://imagebin.ca/view/Uj-KB26v.html](http://imagebin.ca/view/Uj-KB26v.html)

This is at kubuntu at installer step:- (Same is the case with ubuntu)
[http://imagebin.ca/view/wZBYBV.html](http://imagebin.ca/view/wZBYBV.html)

fdisk -l report:-
[http://imagebin.ca/view/CH8fiE6r.html](http://imagebin.ca/view/CH8fiE6r.html)

I tried alternate cd also...no change!

Help Me!

---

### Post by darkod on 2010-06-05
The imagebin website doesn't load. Can you attach the images here? There is button Manage Attachments when creating a post. Don't use the quick post, use the standard form and look little below.

---

### Post by srs5694 on 2010-06-05
I can't be positive, but this may be an example of the problem described [here.](http://www.rodsbooks.com/missing-parts/index.html) If so, that page provides pointers to fixing the problem. If you continue to have problems, please post back with more details, including the output of the "fdisk -lu" command (note "-lu"; "-l" is insufficiently precise).

---

### Post by darkod on 2010-06-05
> **srs5694 said:**
> I can't be positive, but this may be an example of the problem described [here.]("http://nessus.rodsbooks.com/missing-parts/index.html") If so, that page provides pointers to fixing the problem. If you continue to have problems, please post back with more details, including the output of the "fdisk -lu" command (note "-lu"; "-l" is insufficiently precise).

Just a note, that link doesn't seem to load, at least not for me. Maybe they moved something. :)

---

### Post by srs5694 on 2010-06-06
My apologies. It's a link to my own site, but I accidentally posted a link to my internal network rather than the externally-accessible URL. I've fixed it in the original post.

---

