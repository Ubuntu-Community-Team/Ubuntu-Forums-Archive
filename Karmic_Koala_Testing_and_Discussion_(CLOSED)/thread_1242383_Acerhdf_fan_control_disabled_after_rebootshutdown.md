---
title: "Acerhdf: fan control disabled after reboot/shutdown"
date: 2009-08-17
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Sokraates on 2009-08-17
Hello!

I use acerhdf 0.5.17 with the 2.6.31-6-kernel on KNR (Kubuntu Netbook Remix) on an AAO 110.

Compiling and installing acerhdf works fine. I added it to /etc/modules and it loads on startup. 

However /sys/class/thermal/thermal_zone0/mode is per default set to "disabled". So to make fan control and acerhdf work, I neet to do a "sudo -s" (regular sudo won't work) and then "echo -n "enabled" > /sys /class/thermal/thermal_zone0/mode".

Now the problem is that /sys/class/thermal/thermal_zone0/mode is reset to "disbaled" after every reboot or shutdown.

Does anyone have an idea, how to make this change permanent?

Regards,
Sokraates

---

### Post by kozimodo on 2009-08-17
Add 'echo -n "enabled" > /sys /class/thermal/thermal_zone0/mode' to rc.local.

I  also believe that acerhdf now comes pre-built so you no longer need to build it yourself.

---

### Post by Sokraates on 2009-08-17
> **kozimodo said:**
> Add 'echo -n "enabled" > /sys /class/thermal/thermal_zone0/mode' to rc.local.

I  also believe that acerhdf now comes pre-built so you no longer need to build it yourself.

Thank you. Works like a charm. :KS

I haven't found acerhdf in the repos. Is it built into the kernel by now?

---

