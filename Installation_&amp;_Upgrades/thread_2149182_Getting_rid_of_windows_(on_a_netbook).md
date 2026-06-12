---
title: "Getting rid of windows (on a netbook)"
date: 2013-05-28
forum: Installation &amp; Upgrades
---

### Post by Nonc on 2013-05-28
Hey all, 

So I managed to acquire a netbook;

Gateway NAV50, Intel Atom N450, 1GB RAM, No optical drive, preinstalled with Windows

and it came with Windows. I downloaded the lubuntu installer (sort of equivalent of WUBI) and installed lubuntu. Now its not been working perfectly, but its been manageable - It keeps complaining of not enough swap space so it doesn't go to sleep properly. I now want to fix this by getting rid of windows and putting it fully (or at least mostly) lubuntu (and hopefully increasing the size of the swap). But I don't know how to do this since I don't have a CD drive, so I can't mount a live disk and repartition the drives, and I don't have access to a USB thumb drive to do it using that somehow.

Can anyone suggest a solution for me, repartitioning inside the OS, or something else I don't know about?

cheers

nonc

---

### Post by Megaptera on 2013-05-28
I hope this guide helps: "This document describes how to resize a Wubi virtual disk ..." [https://help.ubuntu.com/community/ResizeandDuplicateWubiDisk](https://help.ubuntu.com/community/ResizeandDuplicateWubiDisk)
Without a CD/DVD or USB this looks like a possible answer.

---

### Post by fantab on 2013-05-28
WUBI is apparently being phased out. It is not available with latest Ubuntu 13.04. Its not a longterm solution. Consider getting yourself a USB flash/pen drive.

Do not remove Windows, until you are absolutely certain that Linux will run good on that netbook of yours. Netbooks can have weird Hardware configs. and may not run well with Linux.

---

### Post by Mark Phelps on 2013-05-28
What do you mean by  > (sort of equivalent of WUBI) ??

Wubi installs Ubuntu INSIDE a Windows partition; thus, removing Windows automatically removes Ubuntu as well.

---

