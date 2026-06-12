---
title: "Can i get more than 30gb of space in ubuntu? (dual boot)"
date: 2011-11-24
forum: Installation &amp; Upgrades
---

### Post by animefreak873 on 2011-11-24
hi i have been wubi to install ubuntu but now im installing it on my  netbook that has 200gb harddrive and i want ubuntu to have at least 50gb but wubi has 30gb limit..so i did some resarch and i found out that the only way is with a cd or usb so can i have windows and ubuntu on the same computer if i install by usb or cd?  thanks you

---

### Post by realitykid on 2011-11-24
> **animefreak873 said:**
> hi i have been wubi to install ubuntu but now im installing it on my  netbook that has 200gb harddrive and i want ubuntu to have at least 50gb but wubi has 30gb limit..so i did some resarch and i found out that the only way is with a cd or usb so can i have windows and ubuntu on the same computer if i install by usb or cd?  thanks you

Yes, you can. But you need to shrink the Windows partition first so there is room to install Ubuntu.

[http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/](http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/)

I use Gparted Live CD to partition my drive the way I want it.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

Instructions for setting up a dual boot:


[http://www.muktware.com/man/2684](http://www.muktware.com/man/2684)[]("http://opensource-sidh.blogspot.com/2011/10/install-ubuntu-1110-and-windows-dual.html")

---

### Post by Rubi1200 on 2011-11-25
Hi and welcome to the forums animefreak873 :)

Let me understand this; you had a Wubi install and now want to do a regular install directly to the hard-drive correct?

If yes, then follow the advice posted by realitykid.

If your intention is to keep Wubi but just give it more space, then read here first:
[http://ubuntuforums.org/showthread.php?t=1625371&highlight=wubi](http://ubuntuforums.org/showthread.php?t=1625371&highlight=wubi)

---

### Post by animefreak873 on 2011-11-25
> **Rubi1200 said:**
> Hi and welcome to the forums animefreak873 :)

Let me understand this; you had a Wubi install and now want to do a regular install directly to the hard-drive correct?

If yes, then follow the advice posted by realitykid.

If your intention is to keep Wubi but just give it more space, then read here first:
[http://ubuntuforums.org/showthread.php?t=1625371&highlight=wubi](http://ubuntuforums.org/showthread.php?t=1625371&highlight=wubi)

IM NOT SURE HOW TO DO THIS! um....could you help me in teamveiwer? i now im asking alot for you to go out of your way  but i would really appreciate it.

---

### Post by Mark Phelps on 2011-11-26
Moving a Wubi install to a separate install is a very difficult process -- which is why scripts are used to do the bulk of the work.

I would advise against your doing this, as following the instructions to the letter is really the ONLY way to do this.

Some things in Linux are just really hard -- this is one of them.

Also, do NOT use Gparted to shrink your Win7 OS partition.  Doing so risks filesystem corruption and could render Win7 unbootable.  Instead, use only the Win7 Disk Management utility to shrink the Win7 OS partition.

---

