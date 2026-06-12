---
title: "Disk Utility - palimpsest missing from System &gt; Administration menu"
date: 2010-03-19
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by canter690 on 2010-03-19
Did a fresh install from DVD of Beta 1.  Had previously been testing Alpha 3 and the Disk Utility was there.  

After the install I didn't see the Disk Utility menu item ( not even gparted ).  Thought it might have something to do with dmraid or mdadm not being installed which I then did but still no menu item.

I can start palimpsest from the command line and it works.  Just wondering why it didn't appear in the menu by default.

Not a big issue.

Also would have expected the install to have provided mdadm and dmraid as default.

---

### Post by neglesaks on 2010-03-22
I have trouble with a missing palimpsest as well.

I believe that a library was removed due to dependency problems, and for one, palimpsest is missing in LL Beta 1. What's worse is that I am also unable to mount any hard drives in the gnome sidebar.

Even worse, i get a hard crash when I attach external USB 3.0 store (which worked very well in Karmic, I must add).

Update: Checking in Synaptic, palimpsest requires libgdu0 version 2.29.90, but only 2.28 is available.

---

### Post by canter690 on 2010-03-22
Actually mine is back.  Not sure when but some time after the fixes to nautilus and gnome-panel.

---

### Post by emarkay on 2010-03-22
Anyone getting false Your Disk is Failing" warnings - There's a bug on this?

[https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/438136](https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/438136)

Oh nevermind, looks like it will be fixed in Beta 2.

---

### Post by neglesaks on 2010-03-24
My palimpsest is back and working fine after today's update of libgdu0.

---

