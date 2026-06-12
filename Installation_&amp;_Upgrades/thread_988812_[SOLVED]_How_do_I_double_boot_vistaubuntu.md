---
title: "[SOLVED] How do I double boot vista/ubuntu?"
date: 2008-11-20
forum: Installation &amp; Upgrades
---

### Post by arashiko28 on 2008-11-20
I have a new baby, it's a Lenovo Ideapad Y530, a total beauty, but it came with windows vista home premium. I want to double boot with Ubuntu as usual and eventually delete windows again, but this time I guess would take longer, before I make that jump.

I know the computer is linux compatible, because is all intel. The question is the embedded web cam and the veriface system, that would take a while to confirm.

My main concern is that I have to rezize and partition the C partition to fit Ubuntu, but it didn't came with a recovery CD, it has the onekey recovery wich is supposed to do the same job if the OS gets corrupted by any means.

So, how do I proceed to this double boot installation, I was thinking of choosing a guided (use contiguous space), but would truly appreciate a few guidelines, like the recommended space for vista to work properly.

---

### Post by tuxxy on 2008-11-20
You could use gparted on the Live CD and would need to shrink the current vista partition first then create a new ext3 partition for Ubuntu and select this new partition at installation.

Unless of course you wanted a /home partition aswell which means you would need to shrink the vista and create 2 x ext3, select manual partitioning at install and mount the 2 partitions to / and /home

---

### Post by Partyboi2 on 2008-11-20
I would recommend using the resize tool that comes with vista to shrink down the vista partition before trying to install ubuntu. 
Here is a howto you can follow
[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

---

### Post by Helios1276 on 2008-11-20
You should indeed shrink the vista partition with the tool provided in Vista but it may limit you in how much space you can free up due to a couple of things like pagefiling. I personally turned these off for the duration of the install and then back on again but thats me.

---

### Post by arashiko28 on 2008-11-21
I already did it, it gave 55GB of free space, tried to repeat ir but didn't worked. So, I decided to do it that way. But when I try to install or run live CD, it gives me a message of BussyBox and cone err5 message, doesn't really explain itself, but I can't go on and install. It does takes line commands, so I exit safely by typing reboot.
Please help!!! I miss my ubuntu and my cubes and fire effects![-o<:confused:

---

### Post by arashiko28 on 2008-11-21
I kept trying and got the live CD to boot up. However, couln't do anything, I took this picture with my PPC. This is how the screen looks like. The login screen also looks like this and the transition screen (where some put a splash) looks normal, but then changes back to look like this.:confused:

My video card is a Mobile Intel(R) 4 Series Express Chipset Family

---

### Post by arashiko28 on 2008-11-21
bump! Please help!

---

