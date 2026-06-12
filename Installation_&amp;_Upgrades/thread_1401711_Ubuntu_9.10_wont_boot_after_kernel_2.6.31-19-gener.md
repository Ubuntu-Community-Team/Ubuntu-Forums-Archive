---
title: "Ubuntu 9.10 wont boot after kernel 2.6.31-19-generic upgrade"
date: 2010-02-08
forum: Installation &amp; Upgrades
---

### Post by EdwardMorris on 2010-02-08
This seems like a problem that won't go away. I first saw this one when I upgraded to -16-generic and it blew away my boot menu, but reading around I found a way to manually boot into linux, install grub2 and run update g-grub2 to get my menu back. The same problem occurred with the -17-generic upgrade and I had to boot in manually and do another update-grub2 to restore the menu. Now the exact same problem again except this time update-grub2 is not fixing the menu, and I keep booting into grub and have to maually boot into -17-generic each time, since -19-generic won't even boot, errors out saying "Wrong magic number". Is there a way to undo this upgrade and restore my installation? Its a 64-bit Karamic Wubi install..

---

### Post by beatanga on 2010-02-09
solution found on this topic

[http://ubuntuforums.org/showthread.php?t=1376781](http://ubuntuforums.org/showthread.php?t=1376781)

with this patch for wubildr

[https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210](https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210)

:)

---

### Post by darkod on 2010-02-09
Also, I would recommend next time don't use [ubuntu] mark for your thread because there is a [wubi] mark to use. It will give people idea right away and also might attract people who know wubi to read it (because not a lot people use wubi).

At least you wrote that it's wubi in your post, a lot of people don't mention it and prevent easy help, because this fix for wubildr is not used in full ubuntu by the way, only in wubi.

---

