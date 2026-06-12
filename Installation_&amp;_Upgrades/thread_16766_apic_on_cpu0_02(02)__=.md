---
title: "apic on cpu0: 02(02)  =\"
date: 2005-02-23
forum: Installation &amp; Upgrades
---

### Post by SleepWalkerX on 2005-02-23
i finally got my ubuntu discs that they shipped me and was immediately excited!!  i heard it was the best linux distro.

but then when i tried to run the livecd, i got to the bootloader and it gives me 3 seconds to make a choice then it picks the default one and i get a black screen.  

then i tried the install cd and i get to the press F1 for help and hit enter to boot  screen.  when i hit boot i get the error code apic on cpu0: 02(02) and it repeats like crazy on a black screen.  then i disabled apic in the bios and still get that error (but only faster imo).  then i tried the boot option linux apic=off and still get the message.  

*sniff* i only wanted to get away from windows.  :(

i'm running an ASUS A7N8X-E Deluxe and AthlonXP 3000+ (i'm pretty sure i'm running the latest bios update).   any help would be great.

---

### Post by alastair on 2005-02-23
Try "noapic" as a kernel argument via grub.

---

### Post by SleepWalkerX on 2005-02-23
how do i go about doing this?  i'm really a linux noob.  :(

---

### Post by alastair on 2005-02-23
Ahh ... you said you already tried boot options.

At the prompt for "install", you should be able to enter something like :

linux noapic <enter>

But check the help screen(s).

If you have a boot/grub step (e.g. liveCD), you should be able to hit <ESC> to get a grub menu, choose the kernel, hit "e" to edit and edit the kernel line (<enter> on it) to add "noapic", then <enter>).

---

### Post by SleepWalkerX on 2005-02-23
oh my bad i didn't know it was at the same place.

i tried linux noacpi and it still looped displaying the same message.  but it seemed slower.  

i didn't try it with the livecd.

edit:  btw i tried the livecd on my brother's computer.  he has a k8n neo2 platinum msi board and it worked.  i didn't try the install cd cause i didn't want to bug him.  i'm going to try a bios update again. 

btw i happened to have this problem when i installed windows xp on this hard drive.  it would freeze after "setup is installing windows" after it loaded some drivers.  i had to press F5 before it would load drivers and hit the default 386 installation option and for some reason it worked.

edit2:  i updated bios and disabled apic and had the noapic boot option, but still the same message.

---

### Post by SleepWalkerX on 2005-02-26
^bump  :(

i will love you if you can help me fix this.

---

