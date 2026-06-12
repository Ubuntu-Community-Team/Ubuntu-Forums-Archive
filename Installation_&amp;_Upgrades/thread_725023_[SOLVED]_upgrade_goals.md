---
title: "[SOLVED] upgrade goals"
date: 2008-03-15
forum: Installation &amp; Upgrades
---

### Post by DarinB on 2008-03-15
i want to make upgrades to new versions easy. (even though i did upgrade banzai style and had almost perfect results it was too stressful) who wants to do this every six months because you can't skip interim releases to get to the LTS???
i did read on the forums that putting the home folder on a separate drive will allow me to simply do a fresh install and point to the home folder.
questions ???
will this work?
will all my installed packages need to be reinstalled ?
will my settings remain?
If i add an additional hard drive can i move my current home folder get the system to use it> then delete the original folder?

---

### Post by mikewhatever on 2008-03-15
will this work? --> Yes.
will all my installed packages need to be reinstalled ? --> Yes.
will my settings remain? --> Yes.
If i add an additional hard drive can i move my current home folder get the system to use it> then delete the original folder? --> Yes.
[http://psychocats.net/ubuntu/separatehome](http://psychocats.net/ubuntu/separatehome)

You can also backup /home before reinstalling and then copy it back after.

---

### Post by DarinB on 2008-03-15
so
1 i install new hard drive 
2 mount it 
create mount point???
then move home there as per link above.
**then not sure from here on???????????**
put in Hardy cd (when the stable comes out)
then what clean install on the computer??
will it automatically choose the system partition??
then i think i read that the prompt will ask where to point to the home folder???
not sure  really????

---

### Post by mikewhatever on 2008-03-15
then not sure from here on??????????? --> Start using your new /home.
will it automatically choose the system partition?? --> No, you should go for manual partitioning and point the installer to the right one.
then i think i read that the prompt will ask where to point to the home folder??? --> No, as with the system directory, you'll have to chose /home manually.

---

### Post by DarinB on 2008-03-15
Thanks i guess once i finally do it next month when Hardy is released it will be more clear.

---

### Post by zvacet on 2008-03-15
After you made separate home you can do upgrades with alternate CD without losing data.

---

### Post by DarinB on 2008-03-15
what is alternate cd???
isn't that ubuntu light for older machines????

---

### Post by mikewhatever on 2008-03-15
> **DarinB said:**
> what is alternate cd???
isn't that ubuntu light for older machines????

Yeh, sort of, but it can also be used for off line upgrading.

---

### Post by zvacet on 2008-03-15
> isn't that ubuntu light for older machines????

No,it is not.It can be used for that but that is just part of possibilities.Read [here.](http://releases.ubuntu.com/7.10/)

---

