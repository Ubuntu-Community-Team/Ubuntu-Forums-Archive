---
title: "How upgrade kernel?"
date: 2006-03-15
forum: Installation &amp; Upgrades
---

### Post by Dauphinfay on 2006-03-15
I am trying to find a difinitive guide on how to upgrade the kernel. I have seen several "ways" to do it thanks to google but I want to know what is the proper way to upgrade on an ubuntu system. Currently, I have the stock kernel that came with 5.10 (2.6.12-10-386). I am looking to upgrade to 2.6.15-6 (I need DRI enabled my thinkpad t20). Any help here would be appreciated. TIA****

---

### Post by bluevoodoo1 on 2006-03-15
Try this link, I used its help to compile the 2.6.15.6 kernel.

[http://ubuntuforums.org/showthread.php?t=85064](http://ubuntuforums.org/showthread.php?t=85064)

---

### Post by Dauphinfay on 2006-03-16
I followed the instructions and was able to compile the kernel. Thank you for the nudge in the right direction.

I am, however, having a few issues. 1) I am not sure where to enable DRI after running make menuconfig (I don't see it by the graphics cards). 2) While my wireless network card is detected rather easily under the default kernel, I am not so lucky under the new kernel. Being that this is my first real experience in gnome, I am curious as to whether or not I need to install ndiswrapper (if that is actually how ubuntu is loading my dwl-g630).

---

### Post by bluevoodoo1 on 2006-03-16
You can try and use the search feature after 'make menuconfig'. I think it's either the / or might be the \ button. It should give instructions on the top as to which it is. (It isn't the best search, but it's better than scrolling through countless pages)

---

