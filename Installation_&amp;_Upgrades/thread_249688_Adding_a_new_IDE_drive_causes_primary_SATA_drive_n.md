---
title: "Adding a new IDE drive causes primary SATA drive not to boot"
date: 2006-09-02
forum: Installation &amp; Upgrades
---

### Post by patterbt on 2006-09-02
I have a SATA drive installed on my PC with PCLOS, Ubuntu, and WinXP.  I am using grub to triple boot the system and everything works fine.  The ubuntu partition is the "owner" of the grub boot loader.  I recently tried to add an IDE drive to the primary IDE channel on the mobo.  The IDE channel has a DVD drive set as the primary and the IDE HD as slave.  

When I added the IDE drive and restarted, the system would not boot.  The grub boot menu does not display and the only message I see on my monitor is one that says something to the effect of "No boot sector found, replace with a bootable disk and press any key."  

I assume that I will need to make a change to my grub boot configuration, but am not sure what to do.  Does anyone know how to solve this?  The only thing I can do now is just disconnect the IDE drive to get my system to boot as it did previously.  Thanks!!

Brad

---

### Post by confused57 on 2006-09-02
You might go into your bios at startup, with both drives connected, and see if bios is changing the boot order to boot the IDE first when it's connected.  You might try the IDE hd as master and DVD as slave?  Do you have IDE1 and IDE2 controllers and could put the hd on a primary controller by itself?

---

### Post by patterbt on 2006-09-02
Thanks for the response Confused57, I ended up getting it figured out.  

My bios had detected the new IDE drive and replaced my SATA drive in the bios boot order with the IDE drive.  All I had to do was go in there, and reset the bios so that it was looking at the SATA drive for booting rather than the IDE drive, and it works great now.  

Thanks again,

Brad

---

### Post by confused57 on 2006-09-02
Great...it seemed to me to be the most likely thing that was happening in bios, but you had already figured that out.

---

