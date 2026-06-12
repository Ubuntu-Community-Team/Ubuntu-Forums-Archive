---
title: "hp pavillion dv9003ea ubuntu 7.04 beta adventures"
date: 2007-04-12
forum: Installation &amp; Upgrades
---

### Post by mdfel on 2007-04-12
So far with my experiments: two days ago I succesfully installed 7.04 beta, then made a bios upgrade on my new pavillion dv9003ea (bios release date: march 2007). After that I've managed to boot into my ubuntu partition only one time (out of luck?). 
It seems no matter what combination of NOACPI, NOAPIC, NOSMP, NOAPCI, VGA=791 (this one I tried without even knowing what it means) (tried them all in various orders) I can't boot from grub nor from the live cd. 
Sometimes it locks after the part that says [loading console fonts] (in fact after that it seems there's the apic that probes settings as system manufacturer etc etc), other times it goes beyond that but hangs on a blank screen.
After many unsuccesful attempts today i tried a gentoo 2006.1 live cd, the gentoo live cd has no problems loading, anyway I don't really know gentoo so I only managed to have him destroy my windows partition (by the way I just wanted to format the linux partitions but it attempted a resize wich I wasn't aware of and leaved me with a broken partition table because of an error resizing partitions), right now i'm on system restore.

PS: I tried to install 7.04 beta for amd64, 7.04 beta for x386 and 6.10 for amd64 with no success

I'm sorry I can't be more detailed, is there something more I can try?

---

### Post by blackhole82 on 2007-04-12
Ever since I upgraded my CPU to Amd 64 X 2 and my mobo I've had the same problems installing and booting into Ubuntu.  It does work if I boot with noapic on the install, but I haven't bothered to append that to the boot options when booting from the hard drive.  I tried the amd 64 version as well and it does the same thing.  Ubuntu 6.10 Edgy also has the same problem.  I'd rather not have to disable apic just to run Ubuntu, so for now I'm just sticking to Windows until it gets resolved.  Hopefully it will be fixed by the time Feisty is officially released.  Back before I upgraded my PC Edgy was working fine.

---

### Post by mdfel on 2007-04-19
Great! it worked, I've installed 7.04. 
I only had to boot the live cd with acpi=off option,
then aftert installing and booting from disk when I installed nvidia restricted drivers and restarted X did not start, so I rebooted without the acpi=off option and now it is absolutely perfect.

---

