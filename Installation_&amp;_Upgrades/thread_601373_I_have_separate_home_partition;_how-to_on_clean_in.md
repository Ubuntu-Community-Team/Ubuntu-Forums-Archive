---
title: "I have separate /home partition; how-to on clean install?"
date: 2007-11-03
forum: Installation &amp; Upgrades
---

### Post by strange_cathect on 2007-11-03
There is a lot of information out there about how to create a separate /home partition to plan for future clean installations.  However, there is very little in the way of help for how to actually DO the clean install once you have a separate /home.  

After installing 7.1 I have noticed some weirdness in my OS and I want to do a clean install, without wrecking my /home partition, which lives on /dev/sda4. 

Can someone point me to directions about how to direct the installer so that I don't accidentally wreck my /home partition?

Thanks.

---

### Post by yopnono on 2007-11-03
Just mount your /dev/sda4 as /home in the parition manager and select keep current filesystem *do not format*

---

### Post by philinux on 2007-11-04
I'm thinking on the same lines. Do I need to delete .gnome .gnome2 folders from the live cd or will it just all sort itself out. 

How does fstab get sorted etc?

---

