---
title: "Kernel automatic update to 2.6.20-16.31"
date: 2007-09-10
forum: Installation &amp; Upgrades
---

### Post by Dave / Mosaic on 2007-09-10
Running Ubuntu 7.04 here on an Asus-manufactured laptop sold by ZaReason (ZaReason UltraLap; a.k.a. Asus Z3300Ae).

Everything was working mighty fine until yesterday (Sunday, September 9, 2007),  when I let Automatic Update install a kernel upgrade.  The exact upgrade was from 2.6.20-16.29 to 2.6.20-16.31; the actual changes to my system are just /boot/initrd*** and the kernel headers; /boot/vmlinuz*** was not modified by this upgrade.

Now, there are things wrong with my system, though I'm not completely clear as to what.  The main symptoms I observe are:

1) The laptop will no longer automatically suspend when I close the lid, or when it is idle past the threshold time limit, even though all the "Power Options" settings are the way they should be...

2) The system is also somehow slow and unresponsive, whereas previously it had been nice and quick and snappy...  (I realize this is a vague description, but I haven't yet had time to look at what process(es) may be eating CPU time, etc.) 

Last night I modified /boot/menu.lst to let me boot using the /boot/initrd***.bak file instead, which thankfully Automatic Updates had left there for me.  This change (all by itself) returns everything to it's former, working-properly state.

So, my questions:

1) Does anyone know how I can use synaptic (package manager) or apt-get to reverse the change from 2.6.20-16.29 to 2.6.20-16.31?  I've tried in synaptic to do "Force Version" and such, but the only version that seems to be available in the repositories at this point is the latest one, *.31.  Are *.29 (and other older versions, etc.) archived in some central place that I can access?  Right now, I have a working system by using the initrd***.bak that was conveniently left on my system, but the kernel headers are now in conflict with the running kernel, and also I have no way that I'm aware of to recreate this system from the repositories if I tried to...

2) Has anybody else noticed similar behaviors, from this same kernel upgrade?

thanks much--

--dave

---

### Post by badidea on 2007-09-11
I lost my dial up modem on a Dell 1420n with this upgrade. Is there a way to reverse an auto update?

---

### Post by Dave / Mosaic on 2007-09-11
> **badidea said:**
> I lost my dial up modem on a Dell 1420n with this upgrade. Is there a way to reverse an auto update?

Hi--

Do you know, if you had done the exact same upgrade as me?  (That is, from 2.6.20-16.29 to 2.6.20-16.31; on the other hand, you may have been at a different revision previously.)

You can probably see exactly what was changed when, by looking in /boot, and taking note of the times when the various files were last modified.

I was able to back out the upgrade for the time being, because whatever installed the new kernel, left the old kernel in /boot with a .bak extension, and I reconfigured things to boot from that.  This works as far as running the kernel, etc.; the only problem is that the kernel header files don't match the running kernel on my system now, so I can't build anything new that would need to #include them... Also I'm not aware of any way to reconstruct the .29 version kernel and headers from scratch any more; they don't seem to still be in the repositories, though maybe I don't know how to look properly...

--dave

---

### Post by Dave / Mosaic on 2007-09-12
Bump...

Okay, so I understand if nobody knows about the particular fault I experience with the kernel upgrade.  However:

Can anyone tell me how I can resurrect, and/or rebuild, or download, and reinstall, kernel version 2.6.20-16.29?  When I try to look in the repositories with Synaptic Package Manager, to do a Force Version or something similar to try and reinstall the older version, all that comes up in the list is 2.6.20-16.31...

Is there some general means of downloading historical versions of packages, that I am missing?  Ideally, I'd like the ability to recreate a system as of a certain date; I need to be able to produce multiple systems with exactly the same versions of software, etc.

Any and all suggestions, would be most welcome...

Thanks--

--Dave

---

### Post by badidea on 2007-09-14
Hi, I found in APT by looking at the changes made where the upgrade was. It looks like you could just uninstall the new mod and reinstall the old. I have not done this yet as there may be another workaround to get the modem working.

---

