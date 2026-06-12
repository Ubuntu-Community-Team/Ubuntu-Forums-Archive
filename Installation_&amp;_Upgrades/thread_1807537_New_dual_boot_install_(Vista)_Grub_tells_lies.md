---
title: "New dual boot install (Vista) Grub tells lies??"
date: 2011-07-19
forum: Installation &amp; Upgrades
---

### Post by candtalan on 2011-07-19
Beware.
I have just done a dual boot install of Ubuntu 10.04.2 on a Vista laptop for a friend, and at first restart of Vista (from the new grub menu) things at first appeared to have gone drastically wrong.

I already knew there was a recovery partition on the drive, which I did not disturb.

The grub menu included two Windows entries as expected, for vista: 

Windows Vista (loader) on /dev/sda1 
Windows Recovery Environment (loader) on /dev/sda2 

But I *failed* to notice nor realise the significance of the device names and the partition names which in hindsight do not make sense, and were plain wrong.

To run Vista I had chosen the 'Windows Vista (loader)' (the first entry) and I was dismayed to find a fault recovery screen and system of links was displayed. None of this was useful unless I wanted to get into some heavy resets. I tried one or two items but they resulted in 'no fault found, use other methods' (With implication - you have a big problem my friend).

I will not bore you with detail but after a lot more work and then getting the very same result (!) I then realised that I would have expected to be booting from sda2, not sda1, regardless of whether it was grub labelled as 
Windows Recovery Environment (loader).

So I then chose
Windows Recovery Environment (loader) on /dev/sda2
in the grub list, and normal Vista appeared!
(sigh of relief)

This is such a counter intuitive situation that I wonder if I am not the first person to stumble over this. But why?

What might be causing this? Are the partitions named within Windows in such a way as to mislead grub?

I can now tell the owner (a new Ubuntu user) how to get Vista when they want, but I would strongly prefer to offer them a sensible menu!

How do I now change the displayed grub boot menu to read sensibly before I hand the machine back to its owner family? 
Comments much appreciated.
tia

---

### Post by Quackers on 2011-07-19
Yes, with Vista older versions of grub transpose the two entries. You can fix it by using the guide below or you can live with it. The second is easier :-)

[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

---

