---
title: "upgrade from edgy to feisty"
date: 2007-03-23
forum: Installation &amp; Upgrades
---

### Post by kyruz on 2007-03-23
I tryed the official method to update from edgy to feisty beta. 
```
gksudo -S update-manager -d
```
Update manager didn't find any upgrades.

Then I tryed the official method from yesterday:
Alt+F2
```
update-manager -d
```
Update manager found 986 files to download.
Download (23min. 3mb adsl) and installation took 1 hour and 50 min.
After restart it seems that everything works well. :lolflag: 

I now see that today the official update method is back too: update-manager -d

Network manager work in feisty with the linksys wusb54g ver.4 (Ralink) Didn't work in edgy.

---

### Post by cfgtech on 2007-03-23
You got it to work cool !
I'm trying to upgrade from 6.05 to 6.10 so I can run Beryl.
On my laptop I'm already running 6.10 I wanted 7 but I will wait

---

### Post by kyruz on 2007-03-23
How do you upgrade?
```
gksu update-manager -c
```
Is it working for you?

---

### Post by gm333tb on 2007-03-23
Burnt the CD.  Put in the drive and nothing.  Rebooted...nothing.  Followed instructions  Alt F2  then typed gksu sh/cdrom/cdromupgrade and iget a command not found.  Can anyone help with this?  I need this upgrade to get my wireless card working.  Thanks

---

### Post by zvacet on 2007-03-24
```
gksu "sh /cdrom/cdromupgrade" 
```

---

### Post by kyruz on 2007-03-24
> Burnt the CD. Put in the drive and nothing. Rebooted...nothing. Followed instructions Alt F2 then typed gksu sh/cdrom/cdromupgrade and iget a command not found. Can anyone help with this? I need this upgrade to get my wireless card working. Thanks
Is the iso file OK? Have you veryfied MD5SUM? Do you have the right iso for your computer?

---

