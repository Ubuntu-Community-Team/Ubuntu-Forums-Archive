---
title: "booting: log in fail"
date: 2009-11-07
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by dino99 on 2009-11-07
i've upgraded to Lucid32 from karmic32

so, grub menu offer two kernels right now:

- 31.15 : boot without problem
- 32.2  : gdm does not start, and logging from tty1 does not work !!!
          ( user / password  not recognized)

where can i tweak that ?

---

### Post by hikaricore on 2009-11-07
Why don't you just use the old kernel until there is an update?
Several people have pointed out various issues with the new kernel.

---

### Post by dino99 on 2009-11-07
> **hikaricore said:**
> Why don't you just use the old kernel until there is an update?
Several people have pointed out various issues with the new kernel.

you're right of course, no drama us said above, that's only the way i learn, but some guys said that 32.2 boot fine, so .

---

### Post by VMC on 2009-11-07
It works fine for me:
$ uname -r
2.6.32-2-generic

What do you mean won't boot. Doesn't start or freezes? Does log viewer show any kernel errors?

Try booting using single recovery mode with 32-3 kernel.

---

### Post by dino99 on 2009-11-08
Now 32.2 boot fine

In fact, something was wrong with grub2: i redo os-prober, update-grub2 then reboot: problem is gone ):P

---

