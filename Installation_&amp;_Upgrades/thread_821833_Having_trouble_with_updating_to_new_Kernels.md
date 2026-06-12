---
title: "Having trouble with updating to new Kernels"
date: 2008-06-07
forum: Installation &amp; Upgrades
---

### Post by Huw_Dawson on 2008-06-07
Essentially, I'm running on Kernel .16, because .17 and .18 both crash me to BusyBox on the Ubuntu loading screen.

 I'll try to use recovery mode to find out the cause of it dropping to the shell, but does anybody have any initial ideas why Ubuntu is doing this?

 - Huw

EDIT: I'm using 8.04 LTS on an install inside Windows.

---

### Post by Huw_Dawson on 2008-06-08
Okay, slightly more urgent now. I've been hit by the same problem on Kernel .16, and that means I can't use Ubuntu at all - I'm having to revert to XP.

 Worst thing is, I have no idea what I've done to screw it up. 

 It basically (according to extrapolation I have made from observation of the loading screen and then of what it tells me in recovery mode) just gets onto the loading screen and one of the first commands it runs causes an error - something to do with not being able to find a file because it doesn't exist, so the operation fails, and it shunts me down to BusyBox.

 I'll try and get notes on exactly what it says, but could anyone help me out here?

 - Huw

EDIT: Okay, I've manage to scribble down the exact message:

[I]mount: Mounting /dev/dish/by-uuid/3C60-0F9F on /root failed: no such device
mount: Mounting /root on /host failed: invalid arguement
ALERT! /host/ubuntu/disks/root.disk does not exist. Dropping to a shell![/I]

 Then I end up in BusyBox.

---

### Post by adipradana on 2008-06-10
Same thing happened to me. After i updated and restarted, it kept ending up in busy box. But using kernel .16 still works for me.
Does this happen only when installing from within windows?

---

