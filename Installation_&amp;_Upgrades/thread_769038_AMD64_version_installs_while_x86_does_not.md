---
title: "AMD64 version installs while x86 does not"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by BB_DaKraxor on 2008-04-26
Hi,

I've recently purchased a HP Compaq 6715b laptop with a 64-bit CPU and noticed something really strange.

AMD64 versions of Ubuntu, Kubuntu, Xubuntu, etc. install and work fine, while in x86 versions the SATA driver seems to fail. I ran hdparm -tT /dev/sda from the console after booting with the alternate install CD (I couldn't wait for the desktop CD to boot, it was way too slow), and the results were ~200kB/s. In 64-bit Ubuntu and 32-bit Debian the results are fine: Timing buffered disk reads:  132 MB in  3.04 seconds =  43.38 MB/sec.

Does anyone have any solution to this? I would like to install a 32-bit Ubuntu, is there any way to fix the SATA driver?

---

### Post by Pumalite on 2008-04-26
I have installed 4 Hardy's. 2 32 bit and 2 64 bit. In core 2 Duo and Pentium 4 Prescott. They all work fine. I'd look at the hardware: HP laptops have special problems:
[http://aldeby.org/blog/?page_id=87](http://aldeby.org/blog/?page_id=87)

[https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu](https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu))
[http://www.linuxquestions.org/questions/ubuntu-63/hp-pavilion-dv6000-series-Wireless-driver-issues.-403326/](http://www.linuxquestions.org/questions/ubuntu-63/hp-pavilion-dv6000-series-Wireless-driver-issues.-403326/)
[http://ubuntuforums.org/showthread.php?t=582220](http://ubuntuforums.org/showthread.php?t=582220)
[http://ubuntuforums.org/showthread.php?t=431815](http://ubuntuforums.org/showthread.php?t=431815)

---

### Post by BB_DaKraxor on 2008-04-26
Thanks for the reply,

I followed your links but I couldn't find anything related to my problem. Besides, I think my hardware is has a quite nice support as I had no problem running 64-bit version of Ubuntu Gutsy and Hardy. How come 32-bit version does not support the SATA disk??

---

### Post by Pumalite on 2008-04-26
It does. I have a 32 bit installed in a Core 2 Duo, IntelD975XBX, with 3 SATAII drives.

---

### Post by BB_DaKraxor on 2008-04-28
Alright, do you know any way to diagnose my problem? I have no ideas.

Or is this the wrong place to ask this question?

---

### Post by Pumalite on 2008-04-28
Let's try. Post:
lshw

---

### Post by BB_DaKraxor on 2008-04-28
Thanks, I've attached the output.

---

### Post by Pumalite on 2008-04-28
Have you tried 8.04 32 bit Alternate CD?

---

### Post by BB_DaKraxor on 2008-04-28
I think I have, but to be honest, I'm not sure if it was stable or beta. I'm burning the Xubuntu 8.04 alternative i386 CD right now to see if I'm stupid or there is a real problem here. Be right back in a few minutes.

---

### Post by BB_DaKraxor on 2008-04-28
I've tried, no luck. In the console "hdparm -tT /dev/sda" gives ~200kB/s results for both tests.

---

### Post by Pumalite on 2008-04-28
Well, here you have a collection of boot parameters to try your luck:
[http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO.html#toc1](http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO.html#toc1)
[http://d-i.alioth.debian.org/manual/en.i386/ch05s02.html](http://d-i.alioth.debian.org/manual/en.i386/ch05s02.html)
[http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html](http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html)

[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html)
[http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html](http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html)
[http://www.knoppix.net/wiki/Cheat_Codes](http://www.knoppix.net/wiki/Cheat_Codes)
Try the most common first:
noapic nolapic acpi=off pci=noacpi irqpoll pnpbios=off vga=0x317 vga=791 vga=775

All of them to be tried alone or in different combinations.
Good luck.

---

### Post by BB_DaKraxor on 2008-04-28
Thanks, that will keep me busy for a while... I'll come back whining when I finished trying those boot options. :)

---

### Post by abrarey on 2008-04-29
> **BB_DaKraxor said:**
> Hi,

I've recently purchased a HP Compaq 6715b laptop with a 64-bit CPU and noticed something really strange.

AMD64 versions of Ubuntu, Kubuntu, Xubuntu, etc. install and work fine, while in x86 versions the SATA driver seems to fail. I ran hdparm -tT /dev/sda from the console after booting with the alternate install CD (I couldn't wait for the desktop CD to boot, it was way too slow), and the results were ~200kB/s. In 64-bit Ubuntu and 32-bit Debian the results are fine: Timing buffered disk reads:  132 MB in  3.04 seconds =  43.38 MB/sec.

Does anyone have any solution to this? I would like to install a 32-bit Ubuntu, is there any way to fix the SATA driver?

That's really strange I have the same laptop but I hed installed the 32 bit version without problem. The only issue I have right now is with the wireless, I tried to install the drivers the same way I did in Feisty but it didn't work. But all the other things just work fine.

---

### Post by BB_DaKraxor on 2008-04-29
Did you install 8.04 from CD or upgrade from Feisty?

---

### Post by BarryA on 2008-04-29
I had the same problem as you, the 64 bit version went without a hitch but then came to the 32 bit version I ended up with a massive bold patch on my head (or was there already one but minus a few more hairs)?

The way I resolved the issue

At the screen where you get to try before install or just install choose the option you need and leave it there, then the following

F3 Choose Keyboard

F6 then F6 again, press enter to place an X on 4 of then items except Free Software Only

Press Esc then enter (making sure you have not moved from your original choice otherwise you will have to start all over)

Hope this works just as t did for me

---

### Post by BB_DaKraxor on 2008-04-30
Thanks for the help, acpi=off resolves the problem. But it leads to another: this way I don't have ACPI. Have you managed to have support for both the hard drive and ACPI on 32-bit?

---

### Post by Pumalite on 2008-04-30
You can go ahead and install. We'll sort the problems as they come up.

---

### Post by BB_DaKraxor on 2008-05-01
I've installed Xubuntu, everything works fine with acpi=off option passed to the kernel. Except for the ACPI, of course. Since I have a laptop, I'd really need ACPI for power saving when running from battery.

I installed cpufreq-utils, but can't use them:
```
$ cpufreq-info 
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to linux@brodo.de, please.
analyzing CPU 0:
  no or unknown cpufreq driver is active on this CPU
```

Then I tried loading the powernow-k8 kernel module:
```
$ sudo modprobe powernow-k8
WARNING: Error inserting processor (/lib/modules/2.6.24-16-generic/kernel/drivers/acpi/processor.ko): No such device
FATAL: Error inserting powernow_k8 (/lib/modules/2.6.24-16-generic/kernel/arch/x86/kernel/cpu/cpufreq/powernow-k8.ko): Unknown symbol in module, or unknown parameter (see dmesg)

$ dmesg | tail | grep powernow_k8
[ 6375.286822] powernow_k8: Unknown symbol acpi_processor_register_performance
[ 6545.379265] powernow_k8: Unknown symbol acpi_processor_notify_smm
[ 6545.379364] powernow_k8: Unknown symbol acpi_processor_unregister_performance
[ 6545.379527] powernow_k8: Unknown symbol acpi_processor_register_performance

```

So I think I have to enable ACPI somehow. But without acpi=off kernel option my SATA disk reading speed is ~200kB/s.

What do you suggest now?

---

