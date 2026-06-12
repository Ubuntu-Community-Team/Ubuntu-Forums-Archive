---
title: "Hotplug freeze, fresh install."
date: 2005-08-01
forum: Installation &amp; Upgrades
---

### Post by ginkgo on 2005-08-01
Hi, I'm new to the forum here, and to Ubuntu, but I've been a Debian user for some time I have installed Ubuntu onto my main system(no problems), and have ran the livecd are several others(no problems), and I must say I am very impressed with Ubuntu, however I have one system that refuses to work with Ubuntu, for reasons I haven't been able to determine fully as of yet. Here are the specifications for the system in question:

  Dell Dimension 2350
  Intel Celeron 2GHz
  256MB PC2100
  Videocard 1    -      GeForce FX5500
  Videocard 2    -      GeForce FX5200
  Standard keyboard/mouse
  no other devices attached to this system.

now the problem is that I begin the install everything seems to go fine, up until the time to reboot the first time, at which point it reaches "Starting Hotplug", and the system hangs, now i'm not new to Linux so i did try the various boot options "acpi=off" "noapic" "nolapic" "pci=routeirq", and several others I've stumbled across in various places i tried one by one, and in various setups, I have also tried various settings in the BIOS (ACPI, USB, etc related), and disabling them all together, no luck. Also the system has integrated video i tried removing both video cards and using onboard, still no luck. I noticed on several forums people have similar problems with Dell systems in general, and they blacklisted certain modules, so i tried this as well, no luck. So the only thing i could do was use a live cd that will boot (if you're wondering no the Ubuntu livecd did not work either) like knoppix, mount Ubuntu and remove hotplug all together, so the problem is in the way it is being setup. I have went through the various log files and found nothing, i have google'd, and forum'd until I can google, and forum no more. This system previously ran Debian Sid(with a custom kernel 2.6.12 + ck patches) everything setup manually, but i haven't the time to manage Sid anymore, and Ubuntu is the perfect alternative to doing so. Please any help would be greatly appreciated..

---

### Post by luopio on 2005-08-18
I just installed ubuntu on a friend's laptop (Compaq presario M2000) and the system freezes during bootup (apparently at random times). I'm currently doing memtest and I'll inform if I find a solution.

The bootup doesn't just freeze it also seems to be **extremely slow**.. probably a problem with the amd mobile sempron processor and the kernel support.

---

