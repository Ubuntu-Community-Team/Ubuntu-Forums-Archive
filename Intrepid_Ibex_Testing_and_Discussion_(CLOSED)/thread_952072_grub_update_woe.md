---
title: "grub update woe"
date: 2008-10-18
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Richard-g8jvm on 2008-10-18
Hi
I found the reason that I could not use any of the newer kernels since upgrading to Intrepid is that every time the update-grub is run it
puts the default drive as 1,6 instead of 0,6.

Manually editing  menu.lst allows later kernels to be run , but as soon as a new kernel becomes available and is downloaded , update-grub is run and
the whole thing gets screwed up again.

I moved over from Mandriva a couple of months ago as I need better audio app support.
What I do miss is the very nice boot selection tool, I haven't found any thing that does the same in Ubuntu.

How do I stop update-grub from using the wrong drive, and how to get rid of 
4 kernel versions sitting in /boot


TIA

Richard

---

### Post by yabbadabbadont on 2008-10-18
Please post the contents of your menu.lst file.

---

### Post by caljohnsmith on 2008-10-18
To fix the problem with update-grub using the wrong drive for Ubuntu, all you need to do is change the "#groot=(hd1,6)" line to "#groot=(hd0,6)" in your /boot/grub/menu.lst. Try that, run update-grub again, and Ubuntu will then use (hd0,6).

---

