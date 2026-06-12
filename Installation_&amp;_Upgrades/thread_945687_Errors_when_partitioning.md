---
title: "Errors when partitioning"
date: 2008-10-12
forum: Installation &amp; Upgrades
---

### Post by opothehippo on 2008-10-12
Hello,

I've been using ubuntu for a while, although I'm no expert. Recently I wanted to dual boot ubuntu with vista, so I backed up all my documents (not much) and put vista back on my computer.

I didn't know how to figure out the whole partitioning deal so I just let vista replace everything, and figured that the helpful partioner in the ubuntu install would help me put ubuntu back as the main boot. Whenever I try to shrink to the left the current partition (vista, ntfs, 289GB) it gives me an error messege which just says it failed. 

My plan was to shrink vista to about 100GB, then use the rest for ubuntu. It didnt work, so now I need help. I'm new when it comes to partitioning, so please use weird terms sparingly.

Thanks a lot if anyone can help me.

---

### Post by upchucky on 2008-10-12
get knoppix, then use both partitioners that come with it to do the drive, typically  with windows, gparted fails at the last step, but the other partitioner will finish the job.

only do one partition step at a time, it is possible to confuse either partitioner when it tries to do multiple partition steps all at once.

you will need info to edit grub for the new partitions as grub will get confused

supergrub advanced will fix any errors

if you have trouble search for menu.lst editing, and stage 1 and stage 2 booting on this forum. there are hundreds of posts on how to do what you are trying to do

---

