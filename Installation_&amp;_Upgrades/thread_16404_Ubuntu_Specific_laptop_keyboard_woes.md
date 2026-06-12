---
title: "Ubuntu Specific laptop keyboard woes"
date: 2005-02-21
forum: Installation &amp; Upgrades
---

### Post by pardasaniman on 2005-02-21
Hello all, I have a Toshiba Satellite 2400.  (nobody else does!)
And my keyboard will perform weird things in ubuntu.  

Most annoyingly, if I tap a key once, sometimes it will repeat at least 20 times after I let go of the key.  Other times, it will pause, and then my characters will appear.  

Interestingly, some commands consistently cause this.  For example, I was trying to install ndiswrapper.  Doing an sudo ndiswrapper -l in gnome-terminal will consistently cause my "enter" key to repeat many times.  Rebooting does not help either unfortunately.

---

### Post by pardasaniman on 2005-02-22
I should also note that this occurs on a fresh install without ndiswrapper or anything.

---

### Post by pardasaniman on 2005-03-03
For the record, adding softrepeat=1 to the kernel boot parameters fixes this problem.

---

### Post by alastair on 2005-03-03
Well done for persevering and letting people know the solution. THis was a hard one to figure out.

Good luck from now on!

---

