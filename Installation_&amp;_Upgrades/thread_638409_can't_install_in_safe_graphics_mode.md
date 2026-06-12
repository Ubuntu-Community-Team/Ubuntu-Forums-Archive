---
title: "can't install in safe graphics mode"
date: 2007-12-12
forum: Installation &amp; Upgrades
---

### Post by iambrad on 2007-12-12
i'm trying to install ubuntu on my laptop, and have a problem....i've created the partition (40 gig), and everything is ok as far as i can tell with that.  the problem is that i can only boot into safe graphics mode, and i guess since my laptop is a widescreen it is cutting the bottom part of the install off.  I get to the point of selecting a partition and it tells me that i need to set that partition as a boot partition, but i have no way to see what my options are (i tabbed until i found the continue so i could hit enter),

using a HP pavillion laptop with widescreen display.  If you could tell me how to boot into a setup that recognizes my monitor, or run the setup in a way that i can scroll down, i'd probably be your best friend,

thanks,
brad

---

### Post by logos34 on 2007-12-12
> **iambrad said:**
> i'm trying to install ubuntu on my laptop, and have a problem....i've created the partition (40 gig), and everything is ok as far as i can tell with that.  the problem is that i can only boot into safe graphics mode, and i guess since my laptop is a widescreen it is cutting the bottom part of the install off.  I get to the point of selecting a partition and it tells me that i need to set that partition as a boot partition, but i have no way to see what my options are (i tabbed until i found the continue so i could hit enter),

using a HP pavillion laptop with widescreen display.  If you could tell me how to boot into a setup that recognizes my monitor, or run the setup in a way that i can scroll down, i'd probably be your best friend,

thanks,
brad

open a terminal on the desktop and type:

sudo dpkg-reconfigure xserver-xorg

choose a diff video driver---start with vesa.  Run through the interactive...you can accept the defaults for most of the questions.

If that doesn't work, here's a workaround I've used:

right-click on the empty space on the desktop and realign the top and bottom panels to the right and left sides--this should clear just enough space on the bottom to see the 'continue' and other buttons.

---

### Post by iambrad on 2007-12-12
ok got the alternate cd and it pretty much works, but the partitioner still can't use my partition saying that there are no root files....i would think the installer should take care of that for me, but for some reason no dice....what am i doing wrong here? 
everyone says it's easy, but  this is just insane.

---

### Post by logos34 on 2007-12-12
You should have come to a 'partition disks' screen and indicated the mount point for root as '/'.  SOmehting like this:

> [!!] Partition Disks

You are editing partition #6 of SCSI1 (0,0,0) (sda). No existing file system was detected in this partition.

 Partition settings:

               Use as:                     ext3         
       [COLOR="Blue"]        Mount point:             /            [/COLOR]
               Mount options:         defaults
               Bootable flag:           on

               Done setting up the partitiion
               Copy data from another partition
               Delete the partition


---

### Post by iambrad on 2007-12-12
it's always somethin small.....that got it now if i can just get the network set up and my monitor recognized i will be in good shape  thanks

---

