---
title: "Cannot print following upgrade to 9.10"
date: 2009-12-14
forum: Installation &amp; Upgrades
---

### Post by TAFKARS on 2009-12-14
Hello all
Following upgrade to 9.10 I am unable to print to my networked office printer. All was well with 9.04 prior to upgrade.

I receive the following error, printed on a page in place of the job I submitted:

PCL XL Error
        SubSystem: PAGE
        Error:     IllegalAttributeCombination
        Operator:  BeginPage
        Position:  3

Any thoughts or advice most welcome!

---

### Post by TAFKARS on 2010-01-04
BUMP

Back in the office following the festive break. Am I the only one to have endured this error...?

---

### Post by Bertik on 2010-01-06
> **TAFKARS said:**
> BUMP

Back in the office following the festive break. Am I the only one to have endured this error...?

Me too...

---

### Post by Oilarrak on 2010-01-22
Exactly the same problem here with a Cannon printer but not with other "older" HP printers.

Our brand new office printer is a Cannon ir3245n. It is a multifunction (fotocopier, fax, printer) that uses a system of accounts to let users print. Setting it up was a pain in the... but I got it in 9.04 and worked flawlessly. Now in 9.10 I receive the mentioned error. 
As I said, using other older networked printers (all of them HP) gives no headaches. I am not sure if it is a question of Canon (which uses its own program to set queues) or of Ubuntu.

O.

---

### Post by Oilarrak on 2010-01-25
Hi,

I am not certain if this will be of any use to you, but anyway. I fixed the problem with the ir3245n printer by choosing drivers working with PCL protocol not PXL (aka PCL6, if I am not wrong). The latter worked OK in 9.04, but proved to be useless with this particular printer in 9.10. I think all other printers in our office use PCL (PCL5) protocols...then, maybe that's the trick. As a cautionary note: all our other printers are HP, not Canon.

Cheers,

Oilarrak

---

