---
title: "Can't install Ubuntu on Zepto Titan A15"
date: 2008-08-13
forum: Installation &amp; Upgrades
---

### Post by E-mol on 2008-08-13
I have a wierd problem. :confused:

I have tried installing Ubuntu 8.04 on my girlfriends laptop. But every time i try, the linux-kernel is loaded, the Ubuntu-logo shows, the bar begins moving, and then freeze. I have tried the Ubuntu 8.04 live cd, when it starts up, it acts just like the installation.
I have tried Kubuntu 8.04 and openSUSE 10.3 too, no succes. Kubuntu acts just like Ubuntu (of course) and openSUSE couldn't even load the linux-kernel.
I have tried Ubuntu 5.04 install and there the screen is showing a lot of stripes, right from the beginning. The same happens with Ubuntu 5.04 live cd.
I have tried SLAX while it was loading it freeze after these lines:

  isapnp: Scanning for PnP cards...
  isapnp: No Plug & Play device found

I have tried Knoppix (thinks it was 8.3) too, and that works.
The last thing i have tried was installing Ubuntu 8.04 with:

  acpi=off
  noapic
  nolapic
  edd=on

Then the installation works, but when i restart my computer it freezes in the screen with the Ubuntu-logo, look exactly like under the installation.

The computers specifications is:

  Intel Core DUO T2330 1,6 GHz 53
  2GB (1x2GB) DDR2 PC5300 667MHZ
  667MHz
  250GB SATA 2,5" 5400 RPM
  DVD-RW DL 6xx4W/6xx5WD/2xx5W
  Sis Mirage 3+ 256MB (Shared)

I'm pretty new to linux, (a little month) and only have one friend using Linux, so please, be gentle ;) 

Hope someone out there can help :)

---

### Post by spiderbatdad on 2008-08-13
those boot options you used that allowed for a successful installation need to be added to the /boot/grub/menu.lst file.
The first reboot after installation, you will need to use the f6 option again. Then after the system boots run:```
gksu gedit /boot/grub/menu.lst
```

```
## ## End Default Options ##

title		Ubuntu intrepid (development branch), kernel 2.6.26-5-server
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.26-5-server root=UUID=#'s ro **quiet splash **
initrd		/boot/initrd.img-2.6.26-5-server
quiet
savedefault

```Scroll down to this section, and where quiet splash is highlighted, above, delete quiet splash and add your kernel options. There are other suggestions as well, such as adding you options under kopt further up in the file, but I find this method is more reliable. You might also want to set the value savedefault=true, just above this section.

---

### Post by E-mol on 2008-08-14
Is the kernel options these things i set on by f6?

---

### Post by cariboo on 2008-08-14
HAve you tried booting in safe graphics mode? To do this hit F4 at the menu screen and highlight Safe Graphics mode then hit enter you should be on your way to starting the LiveCD.

Jim

---

### Post by E-mol on 2008-08-14
No matter, i tried, with luck :)

Thank you so much for the help :)

---

### Post by hkb on 2008-08-31
> **spiderbatdad said:**
> those boot options you used that allowed for a successful installation need to be added to the /boot/grub/menu.lst file.
The first reboot after installation, you will need to use the f6 option again. Then after the system boots run:```
gksu gedit /boot/grub/menu.lst
```

```
## ## End Default Options ##

title		Ubuntu intrepid (development branch), kernel 2.6.26-5-server
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.26-5-server root=UUID=#'s ro **quiet splash **
initrd		/boot/initrd.img-2.6.26-5-server
quiet
savedefault

```Scroll down to this section, and where quiet splash is highlighted, above, delete quiet splash and add your kernel options. There are other suggestions as well, such as adding you options under kopt further up in the file, but I find this method is more reliable. You might also want to set the value savedefault=true, just above this section.


I have the same problem on the same laptop and the same hardware but i cant get this to work? How do i enter the terminal before booting or do you do this from the live CD?

---

### Post by hkb on 2008-08-31
double

---

### Post by E-mol on 2008-09-01
Press F6 just after the BIOS-splash :)

That did it for me. (Kepp on pressing as an insane, just to be sure :P ;) )

---

### Post by hkb on 2008-09-04
hmm. i cant get it to work. i'm tapping the F6 button like insane but nothing is happening. I even tried it on my other laptop wich already works fine with ubuntu. but i cant get anything to happen on any of the computers ubuntu just loads and doesent care about anything.

---

### Post by velmont on 2009-03-24
> **hkb said:**
> hmm. i cant get it to work. i'm tapping the F6 button like insane but nothing is happening. I even tried it on my other laptop wich already works fine with ubuntu. but i cant get anything to happen on any of the computers ubuntu just loads and doesent care about anything.

Still a problem?

I want to buy this computer to run Ubuntu on it...

---

