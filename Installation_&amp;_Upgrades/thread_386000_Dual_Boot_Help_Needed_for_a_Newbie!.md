---
title: "Dual Boot Help Needed for a Newbie!"
date: 2007-03-16
forum: Installation &amp; Upgrades
---

### Post by darrenkarp on 2007-03-16
Hi all,

I want to install Ubuntu on my Vista Home Premium PC. I want to have a dual boot menu on system startup. Is this possible? If so, is it very complicated to set up?

TIA
Darren

---

### Post by zvacet on 2007-03-16
No it is not.ubuntu installer guides you and you just reed what are you asked.O.K.
Boot up your Ubuntu CD  and after wile you will get to partition step.From given options choose manualy.You will see your win partition marked as ntfs and free space.in that space you will install Ubuntu.if you have 10 or less GB of free space choose automaticly create partition.If you have more free space  then choose make new partition.Do it like this
1.root / =10GB
2.home =rest of your disc space exept
3.swap =ususaly ramx2 
All partitions have to be in ext3 format.
P.S.Sign partition as root(or home...) is done with mountpoint.When you work on partition you will see menu and one category is mountpoint.Click on it and yyou´ll see all options.Naturaly you pick one you need.Maybe my explanation is seems complicated but when you start you´ll see that is not hard thing to do.
Wellcome to Ubuntu!

---

