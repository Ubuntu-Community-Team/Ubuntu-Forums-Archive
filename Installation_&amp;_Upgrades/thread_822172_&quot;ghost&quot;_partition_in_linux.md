---
title: "&quot;ghost&quot; partition in linux"
date: 2008-06-08
forum: Installation &amp; Upgrades
---

### Post by [z]er0 HP on 2008-06-08
Hey guys i'm looking for a little bit of help.
At the moment i currently have ubuntu installed on an old 120gb IDE hard drive and i would like to migrate my whole current installation with settings and everything to my 500gb sata II drive. I was wondering if there is a way to copy it fully similarly to norton "ghost" 
look forward to your replies
Thanks

---

### Post by avtolle on 2008-06-08
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage) Is this helpful?

---

### Post by zvacet on 2008-06-08
[Remastersys]("http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html")

---

### Post by stchman on 2008-06-08
> **'[z]er0 HP said:**
> Hey guys i'm looking for a little bit of help.
At the moment i currently have ubuntu installed on an old 120gb IDE hard drive and i would like to migrate my whole current installation with settings and everything to my 500gb sata II drive. I was wondering if there is a way to copy it fully similarly to norton "ghost" 
look forward to your replies
Thanks

You can use gparted live cd to do the same thing and gparted is free.

[http://internap.dl.sourceforge.net/sourceforge/gparted/gparted-live-0.3.6-7.iso](http://internap.dl.sourceforge.net/sourceforge/gparted/gparted-live-0.3.6-7.iso)

Easy to use.

---

### Post by CREEPING DEATH on 2008-06-08
You probably want to use the "dd" command, but I'm not very familiar with usage.

CD

---

### Post by [z]er0 HP on 2008-06-08
I finally got around to giving partimage a shot and when i try to restore the image it gives me this error. 
> There was a CRC error in CCheck.
Data may be damaged. Do you want
to continue ?    


If someone could suggest a way of using dd to backup my sdc1 partition onto my sdb1 partition and then one to restore it to sda1.

---

