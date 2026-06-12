---
title: "Master Boot Record needs to be refreshed"
date: 2008-09-10
forum: Installation &amp; Upgrades
---

### Post by weasel7711 on 2008-09-10
I recently installed ubuntu within windows vista since it wouldn't boot from the CD. However this didn't work as when I started ubuntu it would try to install but said one of the commands was broken
So I deleted the folder from the hard drive but the boot record is still there. I want to remove the ubuntu boot selection for when i start my computer and just have windows as the only selection. How do I fix that?

---

### Post by caljohnsmith on 2008-09-10
Try "EasyBCD" from within Vista:

[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

It can easily help you modify Vista's boot loader, which I think is where Wubi installs itself.

---

