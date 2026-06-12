---
title: "error 17 in GRUB loader after deleting Ubuntu partition from XP"
date: 2007-11-25
forum: Installation &amp; Upgrades
---

### Post by scott pruett on 2007-11-25
so my Ubuntu newbness has gotten the better of me & I need some pointers.  I had Ubuntu and XP in a clean little dual boot setup, but I found that I wasn't using Ubuntu much at all on the machine.  My intent was to eliminate the Ubuntu partition, give my full hard drive back to Windows, & then toss Ubuntu on another dedicated machine.

I deleted the partition with Ubuntu on it through Windows' Drive Manager (or whatever it's called).  This didn't give me back the space the partition was taking up; it just wiped it clean.  When I restarted, the GRUB loader gave me an "Error 17" & won't let the system do anything.  Yes, I know I goofed.

I'm not super concerned b/c Windows was operating normally for a while before restarting.  I know my Windows data is still there, but I screwed up whatever the loader process is.  I can't afford to mess up my Win partition, however.  How do I fix this?

My drive: 80gb

XP partition: 40gb
ex-Ubuntu partition: blank (I assume)
some Ubuntu-related partition: 1.xx gb

Thanks much,
Scott

---

### Post by Pumalite on 2007-11-25
[http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)

---

### Post by scott pruett on 2007-11-25
> **Pumalite said:**
> [http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)

So let me get this straight prior to just "trying" a fix.  I need to create a new CD with a new GRUB & then update/reinstall my current one?

> Solutions to this problem are to boot with another GRUB, such as Super Grub Disk, and edit the /boot/grub/device.map and re-install GRUB (to the correct device this time). Here is a link with more details about that, [Editing GRUB's device.map](http://users.bigpond.net.au/hermanzone/p15.htm#device.map)

Probably you would also need to edit your /boot/grub/menu.lst as well.
Don't forget to edit your Debian automagic kernels list too, (in the lower-middle of your menu.lst file), to make the changes permantent over a kernel update. groot=
Then run update-grub, just to make sure.

 How can I get rid of GRUB altogether & just do a straight boot into Windows?  Any tips for completely  (and safely) getting rid of the Ubuntu partition?

Thanks...

---

### Post by Pumalite on 2007-11-25
You can erase it with Gparted Live CD. Then fix Windows MBR with Installation CD or Super Grub.

---

### Post by scott pruett on 2007-11-25
> **Pumalite said:**
> You can erase it with Gparted Live CD. Then fix Windows MBR with Installation CD or Super Grub.

THANK YOU!  This worked like a charm.  I'm back in business. :)

---

### Post by Pumalite on 2007-11-25
You are welcome. Good luck.

---

