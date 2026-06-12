---
title: "Kernel panic - wouldnt load after updates."
date: 2008-07-02
forum: Installation &amp; Upgrades
---

### Post by amityak on 2008-07-02
Hello mates

When i try to load ubuntu it says:

"[21.037100] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)"

Why is that happening? How can I fix it? A simple language will be very appreciated as i'm not a linux profi or something.

My assumption is: I tried yesterday to update packages using dpkg --configure -a or something like that, i dont remember the exact command. For some reason it hung, or seemed so. so i aborted with Ctrl+C.

im using ubuntu 7.10 with KDE

Help?

Thank you all!

Amit

---

### Post by PmDematagoda on 2008-07-02
Are you able to boot Ubuntu properly by using an older kernel in the GRUB(the boot loader) list?

---

### Post by amityak on 2008-07-02
nope
i tried the other options as well and they produce the same error

---

### Post by PmDematagoda on 2008-07-03
> **amityak said:**
> nope
i tried the other options as well and they produce the same error

Do you have the Ubuntu Live CD? If so, boot the Live CD and post the outputs of:-
```
sudo fdisk -l
```
and
```
cat /root-of-ubuntu-install/boot/grub/menu.lst
```

---

### Post by old tech on 2008-07-04
Hi I'm new here.
I have the same problem as above. Every thing was fine until the last update. Not it won't boot. It says: Unable to mount root FS on unknown-block (0,0)

             Jack   Thanks in advance

---

### Post by PmDematagoda on 2008-07-04
> **old tech said:**
> Hi I'm new here.
I have the same problem as above. Every thing was fine until the last update. Not it won't boot. It says: Unable to mount root FS on unknown-block (0,0)

             Jack   Thanks in advance

Did you try booting an older kernel?

---

### Post by old tech on 2008-07-04
No not yet.


   jack

---

### Post by pluto_0 on 2008-07-05
I've had the exact same problem as you guys. I found a solution, and thought I'd share it with you.
What happened was that I upgraded my 7.10 to 8.04 by using network upgrade. Everything went fine, but after I restarted, I had the same error as you: kernel panic, unable to mount root fs on unkown-block(0,0). I was able to boot into Ubuntu using the old kernel, though (normal and recovery).
I searched a lot of forums, including this one, until I found this bug:

[https://bugs.launchpad.net/ubuntu/+source/grub/+bug/222421](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/222421)

As mentioned in the bug report, I inserted the missing line in /boot/grub/menu.lst (by using the Ubuntu 8.04 live CD). And voila, it worked!

Hope this helps.

---

