---
title: "Problems opening Ubuntu"
date: 2012-09-17
forum: Installation &amp; Upgrades
---

### Post by Strav9 on 2012-09-17
Hey

I have Ubuntu installed on my computer. I have used it for an year. but i stopped using it for 2months. Now, when i turn on my pc, and choose Ubuntu (instead of windows) i just doesnt open. The screen turns all black (very very dark purple).
so, i wanted to know what should i do.
and if I reinstall Ubuntu, do i lose all my files i had there, or if is there a way to maintain the same "boot.disk" i had to keep my programs and files.

---

### Post by Bucky Ball on 2012-09-17
Welcome.,

You can boot using the Live image (the install CD/USB) and backup the files you don't want to lose from Ubuntu. If you have a separate /home partition you shouldn't lose them anyhow, just copy them in case. 

During install, if you go that way, choose 'Something Else' at the partitioning part and install Ubuntu directly to the existing / partition and make sure /home is not set to format (if you have one). You will see them there clearly as you will the Win partitions (NTFS). Make sure they are also set not to format (no partition should be by default unless you set it).

The install should then partition, pick up Windows and ask if you want it added to the grub menu. Say yes. 

Couple of questions: Do you remember which version of Ubuntu is installed? Was it working okay last time you used it? You boot and then it's a purple screen, nothing else. When you hit that screen could you try hitting ctrl+alt+F1 then typing 'startx', please?

---

