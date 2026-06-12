---
title: "Gusty install will not update"
date: 2007-12-15
forum: Installation &amp; Upgrades
---

### Post by NoOne2 on 2007-12-15
I installed Gusty on an old 850mhz P-III.

During install for some reason it did not pick up my Ethernet card.  I got an error saying it could not update, this was during the install.

I rebooted after install, got the network card running but now it says the system is upto date and I know its not.

I just finished installing this on a variety of machines to test out and they all took about 150megs worth of updates.

I know its not upto date but it says it is.  I remember during one of the update installs there was a command I had to run in order for the updates to continue but I have no idea what it was.

Even if I try to setup the Nvidia drivers under restricted drivers it won't go out and grab the dependencies.
Thanks

---

### Post by Pumalite on 2007-12-15
How much memory do you have?

---

### Post by NoOne2 on 2007-12-15
The machine has 512 megs.

Here is the odd thing.  I installed G-OS no problem which is built on Ubuntu.

When I installed Ubuntu it recognized the Ethernet card but it would not work.  Once Ubuntu booted after install I had to pick the Ethernet icon at the top right and select Wired Connection.  After I did that the card worked fine.

---

### Post by Pumalite on 2007-12-15
Looks like the update went south.

---

### Post by NoOne2 on 2007-12-15
Fixed it!

I went back into the Update Sources window under Administration and unselected the sources, closed, then re-selected.  When I re-selected it came up and told me I needed to reload the update list.

The odd thing is the ethernet connection went back to not working.  I had to select Wired Connection again, then ran the updates.  

Its updating right now.

I'm sure the video driver will work now too, I'll give it a shot afterwards.

Thanks

---

### Post by Pumalite on 2007-12-15
I'm glad for you!

---

