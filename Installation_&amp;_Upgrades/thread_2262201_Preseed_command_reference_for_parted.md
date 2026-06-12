---
title: "Preseed command reference for parted?"
date: 2015-01-23
forum: Installation &amp; Upgrades
---

### Post by herald on 2015-01-23
Greetings!
   We have a pretty great set up using mini ISOs and a web based preseed creator.  Part of this preseed involves creating a bunch of LVMs for our particular partitioning requirements.  I'd really love to be able to encrypt this Volume Group using LUKS.  Either my Google-fu is weak, or the parted language for D-i is being kept as a closely held secret.  Does anyone out there have any information they are willing to share?

Thanks!
-Herald

---

### Post by MAFoElffen on 2015-01-24
Here is the references I had found:
[http://www.enricozini.org/2008/tips/d-i-conditional-partitioning/](http://www.enricozini.org/2008/tips/d-i-conditional-partitioning/)
[https://wikitech.wikimedia.org/wiki/PartMan](https://wikitech.wikimedia.org/wiki/PartMan)

---

### Post by herald on 2015-01-26
> **MAFoElffen said:**
> Here is the references I had found:
[http://www.enricozini.org/2008/tips/d-i-conditional-partitioning/](http://www.enricozini.org/2008/tips/d-i-conditional-partitioning/)
[https://wikitech.wikimedia.org/wiki/PartMan](https://wikitech.wikimedia.org/wiki/PartMan)

Thanks, I had looked at the second link, but I had not seen the first blog page.  Unfortunately, neither of these resources contain any information on defining encrypted partitions.  I'm fairly certain I can base it an a partman advanced recipe, but the specifics of the recipe are quite mysterious.  I was hoping there would be some sort of documentation describing the language, since it seems to deviate quite a bit from the standard debian installer preseed syntax.

Thanks for the links, though!

---

