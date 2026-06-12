---
title: "seperate HD install"
date: 2007-07-01
forum: Installation &amp; Upgrades
---

### Post by molder34 on 2007-07-01
Hi all.....I am able to run the desktop from the Ubuntu CD I got in the back of a boolk but when I want to install it it only sees my IDE drives and not the SATA drive I have in my machine. What is the procedure to make it give me that cghoice?
Thanks....Mark

---

### Post by logos34 on 2007-07-01
In the menu bar, click on Gparted>refresh.  Anything?

more details please,

What release is the cd?  Feisty, Dapper, Edgy?

Was the sata working in other OS?  Or is this perhaps a new machine/newly added drive?  How is the sata formatted?

---

### Post by Levander on 2007-07-01
It may be that Ubuntu doesn't have the appropriate drivers to recognize your SATA controller.  I'd find out the model and manufacturer of your SATA controller.  You probably have to look in your motherboard manual or the manufacturers website on a page they've made for the motherboard for this information.  Then you need to research Ubuntu, probably just by searching the Ubuntu Forums to see if anyone else is having trouble with it.  Gogle searches will also turn  up info on Linux support for your SATA controller.  

Ubuntu-specific info will be easier to follow.  But, you will also be able to use LInux in general info about the SATA controller.

---

### Post by logos34 on 2007-07-01
You can try this hardware probe from the live cd:

**sudo lshw**

---

