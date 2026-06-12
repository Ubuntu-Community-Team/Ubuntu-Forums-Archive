---
title: "sata pci card"
date: 2008-04-06
forum: Installation &amp; Upgrades
---

### Post by 43longtime on 2008-04-06
I want to just make sure if i buy a sata pci card ([http://www.newegg.com/Product/Product.aspx?Item=N82E16815124022](http://www.newegg.com/Product/Product.aspx?Item=N82E16815124022)) am i going to be able to put use it  on ubuntu. like will i have to use drivers or will ubuntu find them or do i need to find them for ubuntu.

thanks....

---

### Post by asbjorne08 on 2008-04-07
it seems to be supported in linux if you look at the product page:
[http://www.syba.com/Product/Info/Id/52](http://www.syba.com/Product/Info/Id/52)

And the linux serial ATA page ([http://linuxmafia.com/faq/Hardware/sata.html#via6421](http://linuxmafia.com/faq/Hardware/sata.html#via6421)) says that the driver was added in 2005, so it should be save to get working. No warranties though.

-- 
a

---

### Post by StOoZ on 2008-04-07
Well the only thing that I can say is, im using the following pci card:
> Silicon Image, Inc. SiI 3512 SATARaid Controller

and it works perfectly.

---

### Post by 43longtime on 2008-04-07
> **asbjorne08 said:**
> it seems to be supported in linux if you look at the product page:
[http://www.syba.com/Product/Info/Id/52](http://www.syba.com/Product/Info/Id/52)

And the linux serial ATA page ([http://linuxmafia.com/faq/Hardware/sata.html#via6421](http://linuxmafia.com/faq/Hardware/sata.html#via6421)) says that the driver was added in 2005, so it should be save to get working. No warranties though.

-- 
a

thanks for all your help i am going to order the card today.

---

### Post by mmilburn on 2008-04-22
> **StOoZ said:**
> Well the only thing that I can say is, im using the following pci card:


and it works perfectly.

Did you have to perform any additional configuration for this card?  I have a PCI Silicon Image SataLink Card and I can not get it to see the hard drive I have connected to it.  In fact, I can't see the card when I issue a lspci command in the terminal.  Any ideas?

---

