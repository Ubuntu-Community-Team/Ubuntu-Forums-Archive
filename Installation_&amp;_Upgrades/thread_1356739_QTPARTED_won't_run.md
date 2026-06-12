---
title: "QTPARTED won't run"
date: 2009-12-16
forum: Installation &amp; Upgrades
---

### Post by Berry Greene on 2009-12-16
Newbie to Ubuntu but going well. Now need to alter/add new partitions to my HDD and have downloaded QTparted as the tool to do it. However, it will not run. I get the response about a child! Thus: 

Applications > SystemTools > QTParted > Enter

Failed to execute child process "qtparted-root" (No such file or directory)

I tried a re-installation & selected a few extra recommended files but same response.

I am at a loss now. Would someone point the way please.

Please be sure to tell me if this is not the right way to go about getting such information. I sometimes feel quite excluded by assumptions.

Thanking you and in anticipation I remain as before 

Berry

---

### Post by Soul-Sing on 2009-12-16
try: ```
gksudo qtparted
```

---

### Post by darkod on 2009-12-16
Or just try Gparted. You can find it in Software Centre and once installed it's in System-Administration.

---

### Post by mkvnmtr on 2009-12-16
It can not be used on a system that is mounted. If you need to work on your system you will need to use it off of the live Ubuntu disk or download the Gparted disk and boot from that.

---

### Post by Soul-Sing on 2009-12-16
> **mkvnmtr said:**
> It can not be used on a system that is mounted. If you need to work on your system you will need to use it off of the live Ubuntu disk or download the Gparted disk and boot from that.

Agreed, but gparted, or qtparted can give a look at your systempart.

---

