---
title: "Help downloading onto USB"
date: 2011-03-05
forum: Installation &amp; Upgrades
---

### Post by Ranger Mattos on 2011-03-05
I recently started looking at other OS's besides the one I'm most familiar with (Windows XP), and I figured that Ubuntu would be a good place to start. I decided to download it onto my USB so that I can switch between Ubuntu and Windows as needed. But I encountered a problem when trying to download.

It seems that the smallest I can get is the 3-GB Ubuntu. The problem with this is that my USB is only 2-GB. So is there another way to get Ubuntu so that I can switch between that and Windows, or do I need to buy a larger USB?

---

### Post by dabl on 2011-03-05
> **Ranger Mattos said:**
> 

 The problem with this is that my USB is only 2-GB. So is there another way to get Ubuntu so that I can switch between that and Windows, or do I need to buy a larger USB?

It is not possible to actually install the live OS onto less than 4GB and have it run satisfactorily for any length of time (you can't update it, install additional packages, etc. etc. for very long before it outgrows the 4GB).

It is possible to set up an image of the Ubuntu Live CD, which is only about 780MB, onto a USB stick and boot it. It is also possible to set up a "Live CD" on the USB stick by mounting the ISO image, copying all the files out of it, and then installing Grub and configuring it to boot and run as if it were a Live CD.  Unfortunately these "Live CD on a USB stick" methods are not for beginners.  If you want to try the latter approach, here is how (there is no difference in Kubuntu for this purpose):

[http://kubuntuforums.net/forums/index.php?topic=3107512.0](http://kubuntuforums.net/forums/index.php?topic=3107512.0)

---

