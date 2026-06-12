---
title: "update-grub takes ages"
date: 2009-12-16
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by vade on 2009-12-16
Perhaps minutes of pausing between detection of grub entries (kernels etc). Happens with both native and virtual (vmware) installations of daily Lucid. No errors logged anywhere. Anyone else get this behavior?

---

### Post by rbmorse on 2009-12-16
I do if Ubuntu Lynx is installed to a partition on a physical hard drive that is different from the one holding the booting MBR files....i.e., machine boots from (hd0) and Lynx is installed to  (hd2,2).  Update-grub works fine when Lynx is installed to (hd0,2).

---

### Post by zika on 2009-12-16
> **vade said:**
> Perhaps minutes of pausing between detection of grub entries (kernels etc). Happens with both native and virtual (vmware) installations of daily Lucid. No errors logged anywhere. Anyone else get this behavior?Same here. It's been like that for some time, even in Karmic ...

---

### Post by ubername on 2009-12-16
I have the same behaviour both in karmic and lucid, and both with MBR on external HDD and internal HDD

---

### Post by ajgreeny on 2009-12-16
Yes, I agree it is probably a problem of grub being on another physical disk to the OS itself.  I had a similar problem the first time I installed karmic on sdb, but grub2 put itself on sda as the main MBR of the machine.  On reboot after install it took about 30 secs or more from  "Starting grub" appearing on screen to the menu appearing.  I thought something was wrong, but it eventually appeared and worked.

A search of forums gave the reason as the different disks, so I reinstalled grub onto sdb instead of sda, and magically the menu appears instantly as expected first time.

I'm not sure about the update grub you speak of as I didn't have a need to run that with the original setup, having changed the grub disk immediately, but update-grub in karmic is fast, with no difficulties showing.

---

### Post by vade on 2009-12-16
On my system grub and os reside on the same physical disk. So even in that case update-grub can be very slow. I haven't had any other problems with grub, though.

---

### Post by zika on 2009-12-17
> **vade said:**
> On my system grub and os reside on the same physical disk. So even in that case update-grub can be very slow. I haven't had any other problems with grub, though.Same thing. One disk. Very slow begore "Configuring grub.cfg" ... No disk access  before that message ...

---

### Post by trulan on 2009-12-17
I think we're talking about two different issues here.  On the one hand you have slow loading of the grub menu at boot-up if grub is on a different disk than the MBR.  Back in Karmic I fixed that by changing the boot order in my bios.

But if I understand the OP correctly the issue in question here is that it takes a very long time to generate grub.cfg, when installing a new kernel or running update-grub.  I don't have this problem - update-grub runs like it has ever since I first installed grub2, taking maybe fifteen seconds to generate grub.cfg from start to finish, finding all the kernels of my three linux installs and my XP drive.

---

### Post by Gina on 2009-12-17
My update-grub takes minutes too - on single HD :(

---

### Post by ranch hand on 2009-12-17
Wow, I am impressed with the long times.

Have no idea what in flinderation is going on there at all.

I had 18 OS' installed on my test platform for the 9.10-testing cycle.  I do not think it ever took over 90 seconds to generate the /boot/grub/grub.cfg file.  That was with a complete (for all OS') custom menu at the top.

I only have 8 on here this time (so far).

---

