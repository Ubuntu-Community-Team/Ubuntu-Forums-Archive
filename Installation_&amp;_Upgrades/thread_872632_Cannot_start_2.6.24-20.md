---
title: "Cannot start 2.6.24-20"
date: 2008-07-28
forum: Installation &amp; Upgrades
---

### Post by rlgoddard on 2008-07-28
Hi,

I've upgraded to the latest kernel, which is 2.6.24-20.  However, booting into the new kernel gives me a perpetual blank screen.  Booting into recovery mode does not help, either.  In either case, I cannot log into the terminal.  This occurs right after I see the "Starting up..." text.  However, booting into 2.6.24-19 still works fine.

Any ideas how I can diagnose this problem, or how to fix this if someone else already had this problem?

Thanks and take care,
Russ

---

### Post by gjoellee on 2008-07-28
this is a common error for this kernel, you should uninstall it and support this bugreport: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/251344](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/251344)

keep on using kernel 2.6.26-19

---

### Post by PmDematagoda on 2008-07-28
> **rlgoddard said:**
> Hi,

I've upgraded to the latest kernel, which is 2.6.24-20.  However, booting into the new kernel gives me a perpetual blank screen.  Booting into recovery mode does not help, either.  In either case, I cannot log into the terminal.  This occurs right after I see the "Starting up..." text.  However, booting into 2.6.24-19 still works fine.

Any ideas how I can diagnose this problem, or how to fix this if someone else already had this problem?

Thanks and take care,
Russ

What VGA card are you using?

---

### Post by rlgoddard on 2008-07-28
> **gjoellee said:**
> this is a common error for this kernel, you should uninstall it and support this bugreport: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/251344](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/251344)

keep on using kernel 2.6.26-19

Thanks!  What's in the bugreport is exactly what I am seeing right now.  I'll also go ahead and turn off hardy-proposed-updates.

Take care,
Russ

---

### Post by rlgoddard on 2008-07-28
> **PmDematagoda said:**
> What VGA card are you using?

nVidia GeForce 6200A.

Take care,
Russ

---

### Post by PmDematagoda on 2008-07-28
> **rlgoddard said:**
> nVidia GeForce 6200A.

Take care,
Russ

It seems more like a bug with the Nvidia driver than a kernel fault, especially since you get stuck at "Starting up..." which is typical of a broken xorg.conf or a badly compiled Nvidia driver module. If you install the Nvidia driver manually the problem may be solved.

---

### Post by rlgoddard on 2008-07-29
> **PmDematagoda said:**
> It seems more like a bug with the Nvidia driver than a kernel fault, especially since you get stuck at "Starting up..." which is typical of a broken xorg.conf or a badly compiled Nvidia driver module. If you install the Nvidia driver manually the problem may be solved.

I don't think that's the problem... people are reporting the same bug for computers with ATI or S3 video cards.  This appear to be affecting primarily AMD processors, but also a few Intel processors.

Thanks for your help though!  I think I'll stick around for the next kernel upgrade.

Take care,
Russ

---

### Post by PmDematagoda on 2008-07-29
> **rlgoddard said:**
> I don't think that's the problem... people are reporting the same bug for computers with ATI or S3 video cards.  This appear to be affecting primarily AMD processors, but also a few Intel processors.

Thanks for your help though!  I think I'll stick around for the next kernel upgrade.

Take care,
Russ

The ATis may also have the same problem in the form of an incomplete fglrx driver, about the S3s, that may have something to do with the deprecated unichrome drivers.

---

### Post by markbuntu on 2008-07-29
The only problem I had with the -20 kernel was that it did not know what to do with the fglrx (ati) kernel modules so I had to add them manually. It even told me that when it was installing itself.

But, the kernel booted fine and I had no problems except I was unable to enable desktop visual effects which was fixed when I reloaded the kernel modules and rebooted.

I just got an update to the -20 kernel today and again, no problems. It did mention some sort of fix for unichrome.

---

### Post by mordak13 on 2008-07-29
Here's the progress on this bug over at Launchpad: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/251344]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/251344") It's seems there are still other issues. I couldn't get my rt61pci wireless card to work at all and booted back into 2.26.19 to get things back to normal.

---

