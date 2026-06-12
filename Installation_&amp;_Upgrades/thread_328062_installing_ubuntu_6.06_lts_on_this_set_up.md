---
title: "installing ubuntu 6.06 lts on this set up"
date: 2006-12-30
forum: Installation &amp; Upgrades
---

### Post by redenjaja on 2006-12-30
here's my case:

on my winxp:
c: 40G======== 30G for window$ and a 7.97G unallocated... i left this for m ubuntu
d: 120G SATA

how do i install it to the 7.97G of unallocated space???? here's a screenshot on where im stuck.... 

[[IMG]http://img72.imageshack.us/img72/2103/screenshotnd8.th.png[/IMG]](http://img72.imageshack.us/my.php?image=screenshotnd8.png)

---

### Post by kelean on 2006-12-30
What you need to do is click on the unallocated line then on create partition.  Dont forget to create a swap partition as stated at the bottom.  
I hope that helps.

---

### Post by redenjaja on 2006-12-30
uhmmm, can you help me with that? i dont know how to create those partitions..... 

how do i make a root and swap partition?

here's what i did...
1.create a new partion (primary artition, fat32)
2.create a linux swap... 

but on the next page, i cant see the 7G fat32 space?

[[IMG]http://img136.imageshack.us/img136/6034/screenshotulitxn8.th.png[/IMG]](http://img136.imageshack.us/my.php?image=screenshotulitxn8.png)

---

### Post by wpshooter on 2006-12-30
I believe I would use ext3 for #1 if that is to be your Ubuntu partition.

---

### Post by redenjaja on 2006-12-30
why fat32? so i can access it when im on window$

---

### Post by Sef on 2006-12-30
> why fat32? so i can access it when im on window$

Yes, or you can install ext2 or ext3 as well.  Linux and Windows will read both.

---

### Post by redenjaja on 2006-12-30
you mean ext3 can be detected on windows??? hmm ididnt know that:)

---

### Post by kelean on 2006-12-30
By the looks of your second screen shot you did not create the partitions you wanted.  Click the back button and see if the changes are still listed.  If they are please post a screen shot, if not try it again and before you continue post a screen shot.

here is a link that might help you.

[http://www.pcmech.com/show/os/903/](http://www.pcmech.com/show/os/903/)

---

### Post by redenjaja on 2006-12-30
from the link you showed, i have to make 3 partitions?
/
/home
/swap
[img]http://www.pcmech.com/imageview.php?image=4521[/img]

what size can you recommend me for the 3 partitions? the reason im having a hard time right now is because i have to manually partition cause it seems it cant use my 7G of unallocated space automatically... 

and another question, is it ok that both my windows and linux will share the same drive?

---

