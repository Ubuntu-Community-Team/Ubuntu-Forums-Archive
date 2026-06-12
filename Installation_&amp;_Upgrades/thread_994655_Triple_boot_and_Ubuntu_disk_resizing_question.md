---
title: "Triple boot and Ubuntu disk resizing question"
date: 2008-11-27
forum: Installation &amp; Upgrades
---

### Post by kartal on 2008-11-27
Hi

I am trying to install Ubuntu on my Macbook pro. I have MacOs and Xp sp2 installed on it. I have read the Macbookpro Ubuntu install guides. However somethings were not very very clear in that documentation. For example

-Can Ubuntu resizing application resize both Mac and Xp drives during installation?  I need some extra space and I am hoping to use Ubuntu resizer to resize both Macos and Xp partitions.

-Is Ubuntu resizer a non destructive partition-data resizing application? I know nothing is %100 guarantee but ideally this should work right?

thanks

---

### Post by talsemgeest on 2008-11-29
Unfortunately you can only resize EITHER the Mac or the windows partition.

If you choose the resize the windows partition you should be able to do it from the manual option on the ubuntu installer, and it should leave your data intact.

However, if you choose to install it onto your mac partition, you will have to resize the partition using bootcamp first and then install using the "manual" option.

Hope this helps :)

---

