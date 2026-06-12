---
title: "Installing Ubuntu 10.10 over Ubuntu 10.10"
date: 2011-03-25
forum: Installation &amp; Upgrades
---

### Post by GeissT on 2011-03-25
Ok so,

I have a dual booted system (Win7 and Ubuntu10.10) my Ubuntu doesnt boot so i want to reinstall it over the existing Ubuntu Installation.

Is it ok to do this or will GRUB have a fit at me?

~GeissT~

---

### Post by ChipOManiac on 2011-03-25
I've done this several times when I had Windows ©®TM, it did'nt give me any problems. Wait for a few more replies though.

---

### Post by Hedgehog1 on 2011-03-26
You can install Ubuntu over Ubuntu - but you need to tell it to reuse your current Ubuntu partitions.

When you get to here, choose the manual method:

[IMG]http://img829.imageshack.us/img829/4196/02specifypartitons.png[/IMG]

Here is what the allocation screen looks like:

[IMG]http://img27.imageshack.us/img27/6770/03allocdrivespace1.png[/IMG]

First, make your '/' (root) partition:

[IMG]http://img31.imageshack.us/img31/7520/04allocdrivespace2.png[/IMG]

[IMG]http://img130.imageshack.us/img130/9673/05allocdrivespace3.png[/IMG]

Next, set up the swap partition.  This usually sets itself up just fine, but double check it.

[IMG]http://img263.imageshack.us/img263/7656/06allocdrivespace4.png[/IMG]

This brings you to here:

[IMG]http://img34.imageshack.us/img34/6017/08allocdrivespace6.png[/IMG]

[SIZE="4"]**Please install the Boot Loader on /dev/sda !**[/SIZE]

Press "Install Now" and you are on your way.

***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-03-26
In case you have a separate '/home' partition:


[IMG]http://img202.imageshack.us/img202/6828/07allocdrivespace5.png[/IMG]

This separates your documents and 'stuff' from the system files and 'stuff' in the '/' partition.

Here is a view of the final layout of the partitions (you may only have two for Ubuntu):

[IMG]http://img853.imageshack.us/img853/841/10diskutility2.png[/IMG]


***The Hedge***

:KS

---

### Post by GeissT on 2011-03-26
Thanks Hedge.

Would it be easier to find a way to uninstall the GRUB Loader and then Ubuntu?

---

