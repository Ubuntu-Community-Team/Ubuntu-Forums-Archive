---
title: "Fresh start with Ubuntu 10.04"
date: 2010-05-27
forum: Installation &amp; Upgrades
---

### Post by reyquito on 2010-05-27
Hello.

I am in need of some good advice from this gentle community. You'll see, I've been a happy user of Karmic koala for the last seven months. I Recently upgraded to 10.04 Lucid Lynx, and found myself with some major & minor issues wich, nevertheless, I've been able to resolve (at least most of them). The fact is I decided it would be really good to make a new fresh start in ubuntu, installin Lucid from zero. But, the problem is that I don't have another HD big enough to bkup all my media files. 

So, the question is: is there a way to reinstall ubuntu without touching certain folders that exist in the same partition than the OS?

Regards.
Q

---

### Post by ajgreeny on 2010-05-27
In theory, using the live CD you can make a new smaller partition at the start of the disk, taking about 10Gb from the existing root partition, to use as the new root partition.

You can then, again using the live CD, delete everything on the existing partition except for your home folder, and then, when you install the new system, you use the old root partition, now containing only your home files, and set it as your new /home partition.  You will have to choose manual partitioning at that stage, of course, but that is something worth doing anyway.

After doing this you may find that some of your files and folders are in a subfolder of home, also called home, but it should be easy to move them folder by folder if necessary to the root of your new /home partition, making sure you do not format it when you install.   Don't forget all your hidden folders and files when and if you give this a try.

I hope this makes sense to you; it is a bit more difficult to explain than it is to carry out in practice.

---

### Post by reyquito on 2010-05-29
Thanks for your answer, I'll see what I can do. It is a bit complicated, but also did my request.

Regards,
Q

---

