---
title: "Grub getting 2 kernels and installs"
date: 2007-03-17
forum: Installation &amp; Upgrades
---

### Post by gigermunit on 2007-03-17
Ok i was updating on edgy and i check how much space i had left it said 1.5gigs....i didnt think that was right since it only needs  2gigs to install and i put it on a 5gig partition it seems when i boot GRUB detects the older kernel and version and the new ones is there anyway i can remove them from grub and free up the space on the partition.

---

### Post by bulldog on 2007-03-17
Yes,you can,it's recommended however to have a spare kernel in case something goes wrong!!

To remove your 'older' kernels go to the synaptics packetmanager and type in the search box linux-image.
Now you see all the installed images.

Remove the ones you don't use anymore,but be sure you leave the one you're using un-touched .
After removing them,type in a terminal ```
sudo update-grub
``` and your menu.lst is up to date again,and you have some free space back.

---

### Post by gigermunit on 2007-03-17
Thx bulldog

---

