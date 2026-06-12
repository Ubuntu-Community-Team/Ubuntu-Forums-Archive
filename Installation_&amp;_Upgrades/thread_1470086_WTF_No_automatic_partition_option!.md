---
title: "WTF? No automatic partition option!"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by adnafunnyfarm on 2010-05-02
I installed Ubuntu on my laptop yesterday with no problem. At the "Prepare disk space" dialog, I had an option to allow the installer to make my partitions for me. I'm installing from the same disk on my daughter's laptop this morning and the only option is manual partitioning. Since I have absolutely no idea how to do that, I'm a little stuck.

Helps?

---

### Post by adnafunnyfarm on 2010-05-02
Bump...
Still can't find an existing thread that directly addresses this.

---

### Post by adnafunnyfarm on 2010-05-03
Bump again.

---

### Post by mathizo on 2011-05-18
Hi

I know this is an old thread, but it was the first result I got when Googling the same problem, so I thought I should register and post the solution here.

The Ubuntu installer doesn't give the option when you have no *free*, meaning *unformated* space, on your hard disk. So even if you have an empty partition, it may not offer you the auto partitioning option. All you have to do is boot into Windows and open the disk space manager (Windows Vista and Windows 7: Settings -> Control Panel -> Administrative Tools -> Computer Management -> Storage -> Disk Management ), and free up some space by shrinking or deleting an existing volume.

Then run the Ubuntu installer again and it'll be fine.

---

