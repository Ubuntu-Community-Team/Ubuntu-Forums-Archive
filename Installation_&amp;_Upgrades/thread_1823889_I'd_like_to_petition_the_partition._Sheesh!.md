---
title: "I'd like to petition the partition. Sheesh!"
date: 2011-08-12
forum: Installation &amp; Upgrades
---

### Post by bradlees on 2011-08-12
I installed 11.04 to dual boot alongside windows 7. I have a toshiba laptop with 2 125gb hdd. I'd like to split the space between the two os's. However, I have a wubi partition and some other ones I'd like to be rid of. 
When i boot i get four different ubuntu options, a window loader, the grub again. How do I clean this up?

---

### Post by bcbc on 2011-08-12
To uninstall wubi, go to Control panel, Add/remove, "Ubuntu". 

This will delete the Wubi Ubuntu install and any data on it. If you need something from the Wubi virtual partition, back it up first (you can't get it after uninstalling).

It will also stop the boot menus from being shown. By the way those 'four' ubuntus are likely different kernel versions.

---

### Post by bradlees on 2011-08-12
Thanks, I'll try that. 

As I plan on giving each os an equal amount of space, is there any specific scheme you might use in partitioning each drive?

"Honor amongst men, corn as the stalks of this honor, its ears the sweet yellow.":popcorn:

---

### Post by bcbc on 2011-08-12
You can share data between Windows and UBuntu easier on an ntfs partition. If you're planning to use both OSes then a separate data partition is a good idea.

Windows is a hungry OS so it needs a lot more space than Ubuntu. If there is specific data you'll only be storing on Ubuntu, then take that into account.

Other than that non-specific advice - you'll probably have to make some decisions on what your needs are. There are a lot of guides out there. My favourite is this: [http://members.iinet.net.au/~herman546/index.html](http://members.iinet.net.au/~herman546/index.html)

---

