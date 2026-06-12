---
title: "switching from SusE (blah) to ubuntu 8"
date: 2008-09-17
forum: Installation &amp; Upgrades
---

### Post by bmw4l1f3 on 2008-09-17
Ok, so I have had SusE for over a year now, its OK, but I have been playing with ubuntu on a friends computer and really like it.

I want to switch to Ubuntu, completely get rid of SuSe.

I currently have a dual boot with Windows XP,  I would like to also adjust my partition.  I currently have a 80 (windows) 20(linux)  and would like to do 70(windows) and 30(linux)  


how do I go about doing this.  there is nothing i want to save on my linux partion as I backed up the files on a DVD already

thanks for your help in advance

---

### Post by caljohnsmith on 2008-09-17
A good place to start would be to defragment your Windows partition. Once you've done that, from the Ubuntu Live CD:
```
gksudo gparted &
```
And you can use that to resize your partitions. Once you get everything the way you want it, just install Ubuntu. :)

---

