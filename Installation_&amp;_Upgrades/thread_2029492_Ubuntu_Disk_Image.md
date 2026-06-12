---
title: "Ubuntu Disk Image?"
date: 2012-07-19
forum: Installation &amp; Upgrades
---

### Post by ryntak on 2012-07-19
Hopefully someone can help me with this.

Here's what I have done:
1) Started by having Windows 7 on my laptop internal harddrive, and installed ubuntu alongside windows 7 on a 1tb external harddrive.  This was my first taste of any non-windows OS ever.  LOVED IT!

2) So, I decided I wanted to have Ubuntu alongside windows on my laptop, without needing to lug around this external harddrive.  However, the 250 gb harddrive in my laptop was just not big enough (imo) to partition for two OS's.  Therefore, I've purchased and installed a 1tb harddrive into my laptop. 

3) I was able to make a disc image of my 250 gb windows harddrive, and install it into my new 1tb internal harddrive.  I've also been able to install Ubuntu (from my original iso download) onto a partition of the new internal harddrive.

4) The problem, however, is that the new install of ubuntu does not have all of the stuff that I've installed, nor all of the work that I've done, etc.  

Here's the question:  Can I somehow make a disk image of the ubuntu partition of the external harddrive and set it up on the ubuntu partition of the new internal harddrive?  Or do I simply need to go through the process of redoing all of that work ?

Thanks!
ryntak

---

### Post by Quackers on 2012-07-19
Welcome to UF :-)

You could use clonezilla to make a copy of your older Ubuntu partition and restore that copy over the top of your new Ubuntu partition.
Or you could just copy/move or redo the changes you made to your old Ubuntu installation in your new one.

[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by D0natell0 on 2012-07-20
I would also recommend the Clonezilla option. I use it in my day to day work with windows and linux systems. 

Not only will working with images of your drives will be quicker than a direct copy of your large drives, but you'll also have an image to fall back on in case your system gets trashed some time in the future.
HTH.

---

### Post by D0natell0 on 2012-07-20
Also take a look at this - Oldfred's suggestions are very helpful...

[http://ubuntuforums.org/showthread.php?t=2017602](http://ubuntuforums.org/showthread.php?t=2017602)

---

