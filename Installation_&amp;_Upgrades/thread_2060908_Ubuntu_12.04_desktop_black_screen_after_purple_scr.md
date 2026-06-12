---
title: "Ubuntu 12.04 desktop: black screen after purple screen"
date: 2012-09-21
forum: Installation &amp; Upgrades
---

### Post by wazzadaya on 2012-09-21
Hi


First time ever to use Ubuntu.

I'm trying to install Ubuntu 12.04 Desktop from USB. When i try to run Ubuntu from the USB, or try to install it right away, i get to the purple screen with "Ubuntu" and four dots below - after that i get to a black screen and nothing more happens.

Searching for this topic i found a lot of posts where the solution seems to be 'nomodeset', so i've tried to put it instead, after and before 'splash', also with 'quiet' in front of splash - which apparently seems to be the solution here. But it doesn't work.

Am i doing it wrong or could it be something else?

The computer can be seen here under 'specifications': 
[http://www.zotac.com/index.php?product_id=403&page=shop.product_details&category_id=75&flypage=flypage_images-SRW.tpl&option=com_virtuemart&Itemid=100167&lang=en&vmcchk=1&Itemid=100167](http://www.zotac.com/index.php?product_id=403&page=shop.product_details&category_id=75&flypage=flypage_images-SRW.tpl&option=com_virtuemart&Itemid=100167&lang=en&vmcchk=1&Itemid=100167)

The grahic card is: Via Chrome9 HCM (shared)

Thanks a lot!

- wazzadaya

---

### Post by TenPlus1 on 2012-09-21
on the line with splash and quiet you can also add xforcevesa which resorts to a basic vesa screenmode that generally lets you run live cd's ok...

---

### Post by wazzadaya on 2012-09-22
> **TenPlus1 said:**
> on the line with splash and quiet you can also add xforcevesa which resorts to a basic vesa screenmode that generally lets you run live cd's ok...

Works like a charm!

Thanks a lot!

---

