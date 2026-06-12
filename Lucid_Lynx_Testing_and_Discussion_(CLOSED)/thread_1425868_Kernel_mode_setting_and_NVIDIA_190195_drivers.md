---
title: "Kernel mode setting and NVIDIA 190/195 drivers"
date: 2010-03-09
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by doctordruidphd on 2010-03-09
I use the proprietary NVIDIA drivers, because nouveau does not (yet) provide fan control or 3d acceleration. After yesterday's update to the -16 kernel, I cannot get the driver to work unless I specify the 'nomodeset' option at bootup. The computer will apparently boot, but the screen goes blank.
Additionally, I cannot get the 195 driver to install at all; it crashes the whole system (and I do mean crash, requires a hard power down) at the opengl screen. 
Anyone have it working without the nomodeset option?

---

### Post by peepingtom on 2010-03-10
nomodeset is an old option, it does more than disabling kernel mode setting. Nvidia's drivers are not likely to ever support KMS. Boot with acpi disabled AND nomodeset, file a bug report for this regression if it's still applicable after applying updates.

What chipset do you use?

---

### Post by doctordruidphd on 2010-03-10
Thank You for your reply.

> What chipset do you use? 

Not sure exactly, this is the output from lspci:

```
01:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce 9800 GT] (rev a2)
02:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce 9800 GT] (rev a2)
```

> file a bug report for this regression if it's still applicable after applying updates.

Will do.

---

### Post by joske on 2010-03-10
The problem is that the new plymouth splash screen loads the nouveau driver, and that conflicts with the nvidia kernel module. Yesterday I had the same. I switched to the nouveau driver from the xorg edgers PPA, and that was running surprisingly fine.

---

### Post by doctordruidphd on 2010-03-10
I have removed plymouth and nouveau and I am booting without the "splash" option. Already covered that issue, the problem persists.

The ubuntu-packaged nouveau is not useful to me as it does not support acceleration nor fan control (fans are too noisy at full speed). 

The nvidia-current driver in the nvidia-ppa is 195.xx, which will not install either from the ppa, nor from the file downloaded from the NVIDIA website. The only driver I seem to be able to get working is the 190.53 downloaded from the NVIDIA website, and I have to use the nomodeset option to get that to run.

I will see if I can find the xorg-edgers ppa, and try their nouveau driver, as it does not seem possible to install the nouveau driver from ubuntu at this point (one of the dependencies requires the -15 kernel).

---

### Post by doctordruidphd on 2010-03-10
In spite of what I said in the last post, I loaded the nouveau driver anyway. Text size is setting properly (1680x1050) with the gfxpayload option, but I cannot get an x screen resolution greater than 640x480. I have made sure all of the proprietary NVIDIA modules are removed, I have inserted the "mode" lines in xorg.conf, along with the lines needed for nouveau, but I cannot get useable screen resolution. Is there some trick to setting x resolution for the nouveau driver?

---

