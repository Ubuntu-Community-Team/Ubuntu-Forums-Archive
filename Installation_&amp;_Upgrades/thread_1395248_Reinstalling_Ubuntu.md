---
title: "Reinstalling Ubuntu"
date: 2010-01-31
forum: Installation &amp; Upgrades
---

### Post by Reddoug on 2010-01-31
Hi All

   What would be the best way to remove Ubuntu and reinstall it. I have it dual booted with Vista. I am having trouble getting my wireless to work. Shows drivers are install but no configuration files. Files are there for ethernet. I had downloaded and burned the original disk and I have a disk that came with a magazine that I want to try. I tried booting to disk to reinstall it but I am not sure about how to over write the old Ubuntu partition. Vista is 64 bit with 4gb of ram. Is it best to install 64 bit Ubuntu of 32 bit?

Thanks, Doug

---

### Post by oldfred on 2010-01-31
If you have no data or configurations that you want to save you can just use manual install and choose your existing root (/) and swap. Most recommend that you create a separate /home so when you reinstall your settings and data do not have to be reformated. If you want to save data you should copy your /home including the hidden files.  If you do not choose manual install it will usually create another set of partitions depending on what you choose.

---

### Post by darkod on 2010-01-31
Depending what you feel comfortable with. I guess the easiest way is:
Boot with ubuntu cd, Try Ubuntu option, open Gparted and delete the ubuntu partitions (root and swap, plus any extended partition it might have created). Leave that space as unallocated. Click the green button in Gparted to execute your commands. BE CAREFUL NOT TO DELETE YOUR VISTA PARTITION!!!

Then boot again with the cd this time Install Ubuntu option, and tell it to use Largest Available Free space to install. That will install it into the unallocated space you created. In other words, in the same space where the previous install was.

---

### Post by Reddoug on 2010-01-31
Thanks for the quick reply's. I will see what happens. I did delete my Vista partition one time. :)

Thanks, Doug

---

### Post by Reddoug on 2010-02-21
Hi
Thought I would update. Ended up having to wipe my HD and start over. Could not get it to work like I wanted. Ubuntu would not differentiate between recovery partition and Vista partition and it removed the Vista partition. 

Thanks for the help.  Doug

---

