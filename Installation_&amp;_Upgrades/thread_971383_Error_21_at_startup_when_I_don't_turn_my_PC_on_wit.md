---
title: "Error 21 at startup when I don't turn my PC on with my USB drive plugged in"
date: 2008-11-04
forum: Installation &amp; Upgrades
---

### Post by steveyos666 on 2008-11-04
On my main hard drive (which isn't USB, it's sata) I use Vista. I was trying to install ubuntu on my cousin's PC. I burned the disk, then put it back in the drive to test it out. I noticed there's this option to install ubuntu right into windows. I haven't used ubuntu in forever so I figured this meant I could run ubuntu in a virtual machine inside of vista. I still don't know if that's possible so if anyone could give me a tip on that I'd appreciate it since it seems to only be a boot option when I turn the pc on, and that's just weird becuase it says performance is slightly slower but that just seems like a typical dual boot. However, that's not the main problem.

After that, I was still having problems getting ubuntu onto my cousin's pc. So, I figured I'd try to install ubuntu onto my USB drive, through my pc, then just give it to him to boot up from his pc. That didn't work though, because his computer was too old to boot from usb. However now, like I said, I'm getting Error 21 when trying to boot the grub loader or whatever it is when my computer first turns on, unless that USB drive is plugged in. I've even tried uninstalling that in-vista ubuntu install and booting without the USB drive but it still does it. I've tried reinstalling that and it still does it. It seems to somehow rely on that USB drive.



So basically I'm trying to just for now get rid of everything linux/grub/whatever-related so I can just get it back to booting vista normally without needing my USB drive. Once I get that back, can someone tell me if there's a way to run the in-vista install of ubuntu on a virtual machine? That would seem like that's what it's supposed to be for. But at least help me get rid of this Error 21, please.

---

### Post by tvtech on 2008-11-04
21 : "Unknown boot failure"

This error is returned if the boot attempt did not succeed for reasons which are unknown.

 ok so your going to need to repair your MBR on your drive otherwise your ALWAYS going to need the USB key.  you've now set it up so that your MBR automatically redirects your bios too look at the usb key after the MBR. 

you should be able to do this easily probably with a windows install disk, do a little research though on how to fix your windows MBR  you may actually be able to repair it from a live CD, I've never had to fix it though.  I just used the XP install disk to repair my MBR when I broke it.  But I didn't break it with linux I did it the old fashioned way by just being dumb.  which is my usual state of being.

---

### Post by steveyos666 on 2008-11-05
I got it! I had to use some repair stuff with the vista disk and type Bootrec.exe /FixMbr

Thanks a ton man, appreciate the help and the fast reply.

---

### Post by Simplemind169 on 2009-01-31
just for a random hint of info 
Error 21 says that ubuntu can't find your bootloader
in this case if it works when your usb is plugged in, this states to me that the grub (bootloader) is installed on your usb drive...

---

