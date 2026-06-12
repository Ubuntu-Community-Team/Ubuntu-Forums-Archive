---
title: "Severe boot issues after performing an update"
date: 2007-04-27
forum: Installation &amp; Upgrades
---

### Post by YorkieManiac on 2007-04-27
I am relatively new to Linux but had been getting on quite well over the last couple of weeks, however last night that all changed.

I performed an update last night but during that process the computer froze. I left it for half an hour but no joy. The keyboard and mouse were non functional so there was only one thing to do, power it down and hope for the best.

When it rebooted it went into the GRUB boot list, since I have a dual boot system with Ubuntu and Windows, but now I get the error: "ERROR 16: Inconsistent File Structure ..." but occasionally I also get "Error 18: Selected cylinder exceeds maximum support by BIOS" and it will not boot!

This happens in recovery mode as well and in addition I can't boot Windows.

I have tried reinstalling Ubuntu from the Live CD but the gParted tool gets stuck detecting the storage devices so I can't format the partitions. A windows install also fails.

i guess this is either a GRUB issue or a problem with the boot sector of the disk, but since all my data is also on this drive, albeit on a different partition, I don't want to format the entire disk.

Please help.

---

### Post by dcstar on 2007-04-27
> **YorkieManiac said:**
> I am relatively new to Linux but had been getting on quite well over the last couple of weeks, however last night that all changed.

I performed an update last night but during that process the computer froze. I left it for half an hour but no joy. The keyboard and mouse were non functional so there was only one thing to do, power it down and hope for the best.

When it rebooted it went into the GRUB boot list, since I have a dual boot system with Ubuntu and Windows, but now I get the error: "ERROR 16: Inconsistent File Structure ..." but occasionally I also get "Error 18: Selected cylinder exceeds maximum support by BIOS" and it will not boot!

This happens in recovery mode as well and in addition I can't boot Windows.

I have tried reinstalling Ubuntu from the Live CD but the gParted tool gets stuck detecting the storage devices so I can't format the partitions. A windows install also fails.

i guess this is either a GRUB issue or a problem with the boot sector of the disk, but since all my data is also on this drive, albeit on a different partition, I don't want to format the entire disk.

Please help.

Do a forum search for the restore/reinstall Grub instructions using the Live CD.

---

### Post by YorkieManiac on 2007-04-27
Surely if this is an issue with GRUB then I would still have the ability to boot in Windows, especially since I can get past the GRUB screen but Windows seems to hang on the Windows boot screen (the big windows logo with the progress bar).

Also would I not be able to reinstall Windows since that overwrite GRUB.When I reinstall Windows, i can get all the way through the disk configuration screen (fdisk) but it starts to throw errors after I have entered regional settings and time information. It states that it is installing the Network components, but I am aware that what it says it's do9ing and what it is actually doing is very different.

Apologies if I have gone on about Windows in this reply, but I am just trying to understand what has gone wrong and how to recover Linux.

---

