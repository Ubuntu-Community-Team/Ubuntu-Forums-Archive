---
title: "Jaunty installer thinks the CD has been removed from the drive."
date: 2009-03-27
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by MountainX on 2009-03-27
At about 74% through installing the base system, the Jaunty installer thinks the CD has been removed from the drive. The CD has been checked -- it has no defects. 

I'm using the alternate installer (amd64) and manual partitioning. Usually I install an encrypted file system with a separate boot partition. I only have 1 HDD in my computer and 1 cdrom. I've been running Hardy on this computer. (And a few weeks ago I installed Jaunty alpha on my other computer with no problems.)

I tried installing 3 times, the last time I didn't make a separate boot partition and I didn't use encryption at all, just to keep it really simple; yet I got the same error at the same place (all 3 times). 

The Alt-F4 console shows that the installation stops just after it switches from preseed to in-target. It stops at the same place every time. The only way to proceed is to reboot.

The installer won't let me go back or continue because it thinks the disk is missing from the cd drive.

---

### Post by MountainX on 2009-03-29
I am preparing to try the install again. Can anyone suggestion what I should change in order to get around this issue?

---

### Post by cariboo on 2009-03-29
I had the same problem a couple of times, the first time it happened, I just started the install again and it completed. The second time it happened there was nothing I could do to get around it. The only solution I found was to burn the iso at the slowest speed possible. I now burn Ubuntu iso's at 4X and haven't had a problem since.

Jim

---

### Post by MountainX on 2009-03-29
Thanks. So you think this problem could appear even though the CD was checked for errors and passed? Did you check your CDs?

---

### Post by vishalrao on 2009-03-30
could it be: i believe this is listed in the "known issues"... when it mentions /dev/sdX is mounted do not press continue, press "go back" (yes its confusing) then it should work... [http://www.ubuntu.com/testing/jaunty/beta](http://www.ubuntu.com/testing/jaunty/beta)

but strange that it works till 74%...

---

### Post by MountainX on 2009-03-30
> **vishalrao said:**
> could it be: i believe this is listed in the "known issues"... when it mentions /dev/sdX is mounted do not press continue, press "go back" (yes its confusing) then it should work... [http://www.ubuntu.com/testing/jaunty/beta](http://www.ubuntu.com/testing/jaunty/beta)

but strange that it works till 74%...

My issue is that the installer (incorrectly) thinks the disk in /cdrom/ has been removed. Pressing "go back" doesn't work.

Using the same installation CD in another computer works, so it is not an issue with the CD. Plus, I have burned two CDs and they both validate as good and they both stop at exactly the same point on this computer.

---

