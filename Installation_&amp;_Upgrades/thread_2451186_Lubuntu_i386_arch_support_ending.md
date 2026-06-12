---
title: "Lubuntu i386 arch support ending?"
date: 2020-09-29
forum: Installation &amp; Upgrades
---

### Post by Vesa_Vilkki on 2020-09-29
I get this message my old good laptop: I try translate it english:

"This system i386 arch is not available anymore new ubuntu realeses. updates ubuntu 18.04 realese are continued until 26/4/2023. If you install new ubuntu from ubuntu.com/download then new realesed are available."

Im using lubuntu 18.04. i386 arch.

So i keep get updates until 26/4/2023 and its save use this realese?

---

### Post by sudodus on 2020-09-29
There is more information at

- [this thread at Lubuntu discourse](https://discourse.lubuntu.me/t/18-04-support-april-2021/1313)

- [this 'Old hardware' thread here at the Ubuntu Forums](https://ubuntuforums.org/showthread.php?t=2130640)

---

### Post by guiverc on 2020-09-29
I helped test Lubuntu (Xubuntu, Kubuntu..) using 6x x86/i386 only laptops & 2x x86/i386 desktops up to and including Lubuntu/Xubuntu 19.04 which is now EOL, and more recently 18.04.5 which was released last month ([http://fridge.ubuntu.com/2020/08/14/ubuntu-18-04-5-lts-released/](http://fridge.ubuntu.com/2020/08/14/ubuntu-18-04-5-lts-released/)).

For flavors like Lubuntu/Xubuntu/.. full support is only offered for 3 years from initial release, which is April-2021 so it's closer than your April-2023 date.  However 'main' Ubuntu packages (ie. those shared with Ubuntu's GNOME desktop, or Ubuntu Server) are supported until 2023-April as you listed.

You can use the `ubuntu-support-status` to see the support status for your actual installed system.  

For my own thinkpad t43 (running Lubuntu 18.04 LTS) for example, that means 23% of my installed packages are EOL April-2021. Given how I use it I'm currently not worried, but I can deny it access to outside (ie. stop it's access to the internet), or switch it to  Debian 10/Buster if I deem it necessary after those dates (I've *tested* Debian on it & the 8x i386 systems I mentioned I use to test Ubuntu *flavors* with too)

---

### Post by Shobuz99 on 2020-10-05
> **guiverc said:**
> I helped test Lubuntu (Xubuntu, Kubuntu..) using 6x x86/i386 only laptops & 2x x86/i386 desktops up to and including Lubuntu/Xubuntu 19.04 which is now EOL, and more recently 18.04.5 which was released last month ([http://fridge.ubuntu.com/2020/08/14/ubuntu-18-04-5-lts-released/](http://fridge.ubuntu.com/2020/08/14/ubuntu-18-04-5-lts-released/)).

For flavors like Lubuntu/Xubuntu/.. full support is only offered for 3 years from initial release, which is April-2021 so it's closer than your April-2023 date.  However 'main' Ubuntu packages (ie. those shared with Ubuntu's GNOME desktop, or Ubuntu Server) are supported until 2023-April as you listed.

You can use the `ubuntu-support-status` to see the support status for your actual installed system.  

For my own thinkpad t43 (running Lubuntu 18.04 LTS) for example, that means 23% of my installed packages are EOL April-2021. Given how I use it I'm currently not worried, but I can deny it access to outside (ie. stop it's access to the internet), or switch it to  Debian 10/Buster if I deem it necessary after those dates (I've *tested* Debian on it & the 8x i386 systems I mentioned I use to test Ubuntu *flavors* with too)

I think I may be out of luck with **Ubuntu** **18.04.5**. I rec'd the same message about "i386 architecture" and updates.
When I ran an ```
** lscpu ** 
```

This is the result I got:

```
 Architecture:        i686
CPU op-mode(s):      32-bit, 64-bit
Byte Order:          Little Endian
CPU(s):              4
On-line CPU(s) list: 0-3
Thread(s) per core:  2
Core(s) per socket:  2
Socket(s):           1
Vendor ID:           GenuineIntel
CPU family:          6
Model:               42
Model name:          Intel(R) Core(TM) i5-2520M CPU @ 2.50GHz
Stepping:            7
CPU MHz:             2448.946
CPU max MHz:         3200.0000
CPU min MHz:         800.0000
BogoMIPS:            4988.94
Virtualization:      VT-x
L1d cache:           32K
L1i cache:           32K
L2 cache:            256K
L3 cache:            3072K
Flags:               fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp lm constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc cpuid aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx lahf_lm epb ssbd ibrs ibpb stibp tpr_shadow vnmi flexpriority ept vpid xsaveopt dtherm ida arat pln pts flush_l1d 
```

My interpretation is that downloading a fresh 18.04.5 will still **not allow** me to start receiving updates again... True or false?

Shobuz99

---

### Post by CelticWarrior on 2020-10-05
```
[COLOR=#000000][FONT=&quot]CPU op-mode(s):      32-bit, 64-bit[/FONT][/COLOR]
```

You can install 64-bit.

---

### Post by Shobuz99 on 2020-10-05
Thank you!

Do you have a link that has the steps to install the 18.04.5 over the 18.04 version I have now, and then what troubles I need to expect or look out for?

---

### Post by CelticWarrior on 2020-10-05
Any fully updated 18.04 is now 18.04.5.

Install as you normally would and after doing your backups.

There's no upgrade path from 32-bit to 64-bit, it must be installed from scratch.

---

### Post by Shobuz99 on 2020-10-05
Thank you! 

shobuz99

---

