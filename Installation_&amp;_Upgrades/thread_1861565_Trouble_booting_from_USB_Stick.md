---
title: "Trouble booting from USB Stick"
date: 2011-10-15
forum: Installation &amp; Upgrades
---

### Post by Tycho59 on 2011-10-15
I'm trying to setup a usb stick into a bootable utility usb to use on my pc as well as pcs belonging to other people.

My problem is that even though the installtion/copy process of putting xubuntu onto the usb stick is successful, i cannot get my computer to boot from it.

My Xubuntu machine is a 3.2 GHz P4 IBM Think Centre.

Thanks in advance for all help

Tycho

---

### Post by mörgæs on 2011-10-15
How did you create the USB stick?
How did you confirm that the process is successful?

---

### Post by Tycho59 on 2011-10-15
I had used the startup disk creator.  It states everything is successful at the end of the process. but it doesn't matter now.


I figured out why I was having trouble getting my comp to boot from usb.  1) The 4GB stick i was using is a sandisk n cant remove the u3 sector(s) from it 2) I used my 8gb sandisk that i was able to remove the u3 sector(s) 3) I had to enable a 2nd bootable hard drive option and put it before the internal hard drive in the primary boot sequence under bios.

---

### Post by mörgæs on 2011-10-16
Good you got it working.
There is some advice for removing U3 in the link in my signature (long post).

---

