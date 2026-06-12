---
title: "Help! Always 100% CPU load after upgrade"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by alsan on 2008-10-31
Hi,

I'm just upgrade from Ubuntu 8.04 to 8.10. After upgrade, the CPU loading is always keep at 60% and above, 100% mostly.

Here is my brief HW config:

Machine: HP Compaq 6515b
CPU: AMD Turion 64
Display card: ATI x1200
Monitor: 2 (built-in & external LCD)
Display driver: ATI proprietary driver

I'm suspecting that the loading is from the display driver, cause the loading would gain high if I'm running a process with display output, and reasonably low in text mode (comparing using lynx & ff to access localhost website).

Please kindly point me the right way for this, thanks in advance.

---

### Post by alsan on 2008-10-31
Thanks god! Everything back to normal when I reboot my machine with kernel 2.6.24-21.

Then could I say, the new kernel is not working with the ATI driver?

---

### Post by alsan on 2008-10-31
> **alsan said:**
> Thanks god! Everything back to normal when I reboot my machine with kernel 2.6.24-21.

Then could I say, the new kernel is not working with the ATI driver?

After switching back to the old kernel, I can start my XP VM as normal, but all arrow keys can't work!

As my experience, reconfig the VMware is needed, but it need the old kernel header. So, now how can I get the old kernel header back?

---

### Post by Dumdideldum on 2008-10-31
To check what is causing the high CPU load, run the command top in a terminal which displays the current process usage.

To get the kernel headers for your kernel you have to know the kernel version first. 
Run:
uname -a

You'll see for instance:
```
Linux amd64 2.6.24-21-generic #1 SMP
```

So to install the headers for the kernel, run:
```

sudo apt-get install linux-headers-2.6.24-21-generic linux-headers-2.6.24-21
```

---

### Post by speed32219 on 2008-10-31
Dumdideldum

Thank you for that little tidbit of info.  I did not know how to do that.

---

### Post by agentnixon on 2008-11-01
Yup this happened to me, too. After reboot, it went back to normal, but I'm afraid that the problem might not be solved indefinitely. 
I'm running on a Celeron based laptop.

---

