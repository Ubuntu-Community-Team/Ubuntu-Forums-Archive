---
title: "LVM in Ubuntu 5.10"
date: 2005-10-25
forum: Installation &amp; Upgrades
---

### Post by yehbob on 2005-10-25
Hi,

I've done a fresh install of Ubuntu 5.10 yesterday,
When I tried to set up my partitions manually, I found out that  Ubuntu was supporting LVM.

[B]Does someone as already use LVM with Ubuntu ?
What are the advantage of this tool ?[/B]
I never use it and I barely know what it can do.
I suppose it allow to use a mix of different file system or hard drive.

Thanks

---

### Post by mchatel on 2005-10-25
I can confirm that I've been using LVM (logical volume management) since Ubuntu 5.04 (Hoary).  It was available then.  I haven't had to delve into LVM management though yet.  

The advantage of LVM, is that you can more easily re-size your various Linux volumes, if they use LVM, without having to re-partition all the time.

I'll let other more knowledgeable users comment on LVM specifically.  

FYI, I haven't converted to Ubuntu 5.10 yet (Breezy), but am thinking of doing so very soon.  I plan on using LVM then too.

---

### Post by cstudent on 2005-10-25
Can't LVM be used to make Ubuntu "see" multiple drives as one? I don't know much at all about it, but just from snipets I've read, I'm under the impression that this is true. I'm going to upgrade my main computer from 5.04 to 5.10 soon with a clean install. When I do I'm going to add another hard drive. If LVM can make the two drives look like 70gb instead of 40 & 30, this is what I want to do. If anybody can point me to some good links, post, how-tos, etc it would be appreciated.


Bill

---

### Post by bonifacio on 2005-10-25
It was my first time to use LVM.  My decision was based entirely on the flexibility of resizing my logical volume.  I'm not on that point yet that I need to resize but It's good to know that I will have that capability in the future.

Here is a link you might find useful.  [http://www.tldp.org/HOWTO/LVM-HOWTO/](http://www.tldp.org/HOWTO/LVM-HOWTO/)

---

### Post by yehbob on 2005-10-26
Thanks for the tips.
I think I will try LVM this week-end.

---

