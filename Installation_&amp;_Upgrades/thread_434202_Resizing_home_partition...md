---
title: "Resizing /home partition.."
date: 2007-05-05
forum: Installation &amp; Upgrades
---

### Post by EmilyRose on 2007-05-05
So, I want to resize my /home partition so that it becomes 30-40 odd gigs instead of the current 20.. I tried to do it in partion magic 5.0 (what I"ve pretty much always used...) and (I assume) because it is a logical/extended partition it won't let me resize/move it only delete/format - neither of which I want to do!! Is there a way to make it bigger w/o losing everything on it?? If so, how?

Tons of thanks in advance!!

Oh, I'm running Ubunut 6.10 incase that matters...

---

### Post by confused57 on 2007-05-05
You could try the gparted live cd(45 Mb download):
[http://gparted.sourceforge.net/screenshots.php](http://gparted.sourceforge.net/screenshots.php)

Resizing your /home partition may change the UUID of the partition, which would affect the mounting of your /home in /etc/fstab...I'm not sure.   If it did, you could always mount your newly resized /home with the live cd and determine the new UUID & make the change in your fstab...or you could possibly replace the UUID entry in fstab with /dev/hdax(or whatever partition is your home), before resizing.  After resizing, you could always determine the new UUID & enter it in your fstab...I could be wrong though, the UUID may not change, but it's something you might need to be aware of.

---

