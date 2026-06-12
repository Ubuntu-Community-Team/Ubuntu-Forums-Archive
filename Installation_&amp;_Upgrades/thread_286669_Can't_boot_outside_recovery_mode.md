---
title: "Can't boot outside recovery mode"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by kkinder on 2006-10-28
Having resolved edgy breaking my x config, I've moved onto the issue that I can't boot (any kernel) outside of recovery mode. It just has a flashing cursor in the upper-lefthand corner of the screen and hangs until I force-poweroff.

I get the feeling it's that splash screen, although it worked in dapper.

---

### Post by lloyd_b on 2006-10-28
Have you tried <Ctrl><Alt><F2> to see if you can get to one of the virtual consoles?  It may be that the computer is booting, but you still have an X related problem that's messing up GDM (Gnome Login Manager).

Lloyd B.

---

### Post by seldon77 on 2006-10-28
ive got this too...

6800GS Nvidia card, (on dapper - nvidia driver, but nv also works)

the boot cd starts up, splash shows up fine, and then when Gnome is meant to start, the screen is just a mess of weird colours and seems to hang.



> **kkinder said:**
> Having resolved edgy breaking my x config, I've moved onto the issue that I can't boot (any kernel) outside of recovery mode. It just has a flashing cursor in the upper-lefthand corner of the screen and hangs until I force-poweroff.

I get the feeling it's that splash screen, although it worked in dapper.

---

### Post by lloyd_b on 2006-10-28
Seldon77,

Try using the "Alternate" install CD, rather than the "Live" CD.  It uses a text-based installer that's a good deal more robust than the LiveCD.

Lloyd B.

---

### Post by kkinder on 2006-10-29
> **lloyd_b said:**
> Have you tried <Ctrl><Alt><F2> to see if you can get to one of the virtual consoles?  It may be that the computer is booting, but you still have an X related problem that's messing up GDM (Gnome Login Manager).

Lloyd B.

No, that doesn't work. It's not doing anything -- no hard disk spin or anything. If I remove "splash" from the grub config, it works fine. So it's usplash.

---

