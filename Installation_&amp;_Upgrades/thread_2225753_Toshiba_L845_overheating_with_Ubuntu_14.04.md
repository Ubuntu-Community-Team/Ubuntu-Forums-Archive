---
title: "Toshiba L845 overheating with Ubuntu 14.04"
date: 2014-05-23
forum: Installation &amp; Upgrades
---

### Post by hsaltiel on 2014-05-23
Hi!
I recently bought a new Toshiba L845 Laptop, and installed Ubuntu 14.04 64 bits there.
I can work perfectly, and almost everything seems to work perfectly. 
But when I say "almost", is because the laptop overheats after a couple of hours working, executing "sensors" show me that the temperature is almost 90° (Celsius), and I don't see what to do to avoid this, and automate the startup of the fans.
Executing "top" there is nothing using more than 5% of the CPU, and this when I open Thunderbird. Closing it, nothing using more than 1% of CPU.
Is there any way to start the fans, even manually, to avoid shuting down the machine, and waiting an hour, or booting into Windoze to cool my system, and the going back to GNU/Linux?
Thanks a lot in advance for any ideas anybody could have.
Best regards,

HeCSa.

---

### Post by furtizberea on 2014-05-28
Hi,

I have the same problem and the solution for me was unistall acpi package, and install thermald package. I post the solution on your post on [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1322789](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1322789).
Best regards

---

### Post by furtizberea on 2014-05-29
> **furtizberea said:**
> Hi,

I have the same problem and the solution for me was unistall acpi package, and install thermald package. I post the solution on your post on [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1322789](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1322789).
Best regards

Yesterday everything seemed to work properly, but today again the fans began to malfunction.
I followed the steps in this post [http://www.webupd8.org/2014/04/prevent-your-laptop-from-overheating.html](http://www.webupd8.org/2014/04/prevent-your-laptop-from-overheating.html) to activate the drivers intel_pstate, instead of acpi_cpufreq, and now everything seems to work fine. Restart the system a couple of times, and the fans do not spin out of control.

---

### Post by furtizberea on 2014-05-31
Now the CPU temp appears to be controled under 60 ºC, (think still high), but I still wonder who controls fan speed, thermald or BIOS? Since no pwm-capable sensor was found.
I suspect that is the BIOS, but I'm not sure.
Unfortunately I haven't installed windows 8 to see what is the temperature of the processors in that case.

---

