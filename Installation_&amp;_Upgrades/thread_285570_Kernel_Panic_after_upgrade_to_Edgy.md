---
title: "Kernel Panic after upgrade to Edgy"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by squeky on 2006-10-27
Spent all night downloading and installing all the new Edgy updates, everything seemed to have gone smoothly.  Rebooted with the installer, select the 2.6.17-10-386 kernel and get an error:

```
<0>Kernel panic - not syncing:  Attempted to kill init!
```

Recovery mode, same deal.  The "generic" kernel doesn't work either.  Go to select my old kernel from 6.06 I had used up until this afternoon--(2.6.15-27-686) in normal mode and it hangs.  In recovery mode it hangs on:

```
Begin:  Waiting for root file system
```

Hard drives are detected fine and there's no reason to believe it's a drive problem.  Does anyone have any suggestions?  Thanks.

---

### Post by Qazer on 2006-10-27
Same problem here, borring!

If you find a solution, please write it here!

Thanks

---

### Post by frodon on 2006-10-27
See this page to see if you own one of the hardware who creates problems : [https://wiki.ubuntu.com/EdgyKnownIssues](https://wiki.ubuntu.com/EdgyKnownIssues)

see also :
[https://launchpad.net/distros/ubuntu/+source/linux-meta/+bug/68371](https://launchpad.net/distros/ubuntu/+source/linux-meta/+bug/68371)
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/68276](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/68276)
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/68263](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/68263)
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/66837](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/66837)
[https://launchpad.net/distros/ubuntu/+source/linux-meta/+bug/65710](https://launchpad.net/distros/ubuntu/+source/linux-meta/+bug/65710)
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/66479](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/66479)
[https://launchpad.net/distros/ubuntu/+source/linux-meta/+bug/66140](https://launchpad.net/distros/ubuntu/+source/linux-meta/+bug/66140)
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/65710](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/65710)
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/63134](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/63134)

---

### Post by squeky on 2006-10-27
Thanks much for the links frodon.

My problem was the VIA chipset/ACPI issue.  Added "pnpbios=off acpi=force" flags to the grub kernel command and I'm writing this in Edgy :p .  Thanks again frodon.  Hopefully this will help someone else too.

---

### Post by frodon on 2006-10-27
Glad to know that you solved your issue, there's almost always a solution and launchpad is a great ressource that we all should use it bit more.

Enjoy your edgy box ;)

---

### Post by eamann on 2006-10-28
Hi!

I've got the same problem! Stayed up to 2h00 downloading the update only to discover that Ubuntu would not reboot. The error message said:
"Cannot open root device "UUID....." 
Please append a correct "root=" boot option
Kernel panic....."

I'm using an Acer Travelmate 800 laptop. I installed Dapper from a CD with no problem. The monitor is a Mobility Radeon 9000.

I've just migrated from Windows to Linux and would appreciate a newbie-level explanation.

I've tried typing on the screen after the flashing monitor at the end of the text on the screen but I cannot enter any text.

If the solution is very technical I will use Windows (that's how I am connected now to this forum) until I go to an install party at my local LUG.

Best wishes,

Eamann

---

### Post by Daveski on 2007-03-16
> **squeky said:**
> My problem was the VIA chipset/ACPI issue.  Added "pnpbios=off acpi=force" flags to the grub kernel command and I'm writing this in Edgy :p .  Thanks again frodon.  Hopefully this will help someone else too.

I have a machine with a VIA KT400/KT600 chipset. Edgy 2.6.15 kernel worked fine on this system, but the 2.6.17 caused a kernel panic.

Adding acpi=force option to the 2.6.17 kernel options in **/boot/grub/menu.lst** solved the problem and the machine works fine now.

I am just posting this to assist others who search for an Edgy kernel panic on a VIA board. (Kernel panic - not syncing:  Attempted to kill init!)

```
sudo gedit /boot/grub/menu.lst
```

Change to read like this:

```
title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda1 ro **acpi=force** quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot
```

---

