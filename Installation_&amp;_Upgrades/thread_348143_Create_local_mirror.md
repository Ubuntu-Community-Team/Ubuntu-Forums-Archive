---
title: "Create local mirror"
date: 2007-01-28
forum: Installation &amp; Upgrades
---

### Post by tall-male on 2007-01-28
How can I create (download) my own local mirror only for X66 or AMD64? Yes, could do a 
  rsync://archive.ubuntu.com/ubuntu

However, that will take 170 GB of diskspace and I only need X86 or AMD64.:(  
Which directories should I download?

Any ideas?

---

### Post by andrewmcgilvray on 2007-02-05
I am looking to do the same thing but I would also like to restrict my mirror to edgy and feisty? Can anybody help?

---

### Post by andrewmcgilvray on 2007-02-21
So is there no way of doing this? I just cannot figure it out ..

---

### Post by ximok on 2007-03-23
Debmirror to the rescue!

[https://help.ubuntu.com/community/Debmirror](https://help.ubuntu.com/community/Debmirror)

This document may help you folks out.  Instead of using Rsync,which likes to grab everything, you can use debmirror and just grab a specific archive.  I believe you may be able to specific enough to just grab the x86 or whatever platform of a specific release. Just don't forget to grab the common packages as well.

---

