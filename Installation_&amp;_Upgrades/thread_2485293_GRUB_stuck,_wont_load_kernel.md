---
title: "GRUB stuck, wont load kernel"
date: 2023-03-25
forum: Installation &amp; Upgrades
---

### Post by gulsrb on 2023-03-25
Hello everyone,

On a system with multiple OSs (Lubuntu 12.04 and 22.04, Windows7) i have a problem loading 12.04 (i need it for some version specific work).

I tried boot-repair here are my logs:
[https://paste.ubuntu.com/p/g7PNCxbR6H/](https://paste.ubuntu.com/p/g7PNCxbR6H/)

Grub loads, i see the menu, when i select 12.04 (both recovery and regular) kernel does not load at all, it hangs on black screen. 
So I enabled debug output in grub, the screenshot of the line where its stuck is attached. 

Any help or suggestions would be very appreciated,

Thanks.

---

### Post by oldfred on 2023-03-25
You typically need to have a Linux distribution that is newer than your hardware.
That is so kernel, drivers & other support software can be updated to support that hardware.

You show an UEFI system with BIOS installs.
So system is newer than the obsolete 12.04, and should not be expected to work.
You might try a virtual install as that uses its own drivers, but I do not know about virualbox or other options.

Better question would be why 12.04 and find a solution using your 22.04 install.

Long term you should plan on converting to gpt partitioning & UEFI boot, but that will erase system, so good backups are required.

---

### Post by MAFoElffen on 2023-03-26
> **gulsrb said:**
> Hello everyone,

On a system with multiple OSs (Lubuntu 12.04 and 22.04, Windows7) i have a problem loading 12.04 [COLOR=#ff0000]**(i need it for some version specific work).**[/COLOR]

I do DEV?Testing and run across times when I need to do something that requires a specific release version, specific processor or specific arch. I simulate the sandbox and spin up a Virtual machine within it...

Just by coincidinence, My Ama-Gi Project, which the UbuntuForums 'system-info' script came from, was written with other scripts, on a distro I based on Ubuntu 12.04... So I have a 12.04 VM of it. 

Have you thought about installing QEMU/KVM with Virtual Machine Manager? That way you could create a VM, that boot from Legacy/CSM, and keep it safe from the outside world? That way, you could also, easily take VM snapshots, while you are doing your "version specif work."?

---

### Post by gulsrb on 2023-03-27
> **oldfred said:**
> You typically need to have a Linux distribution that is newer than your hardware.
That is so kernel, drivers & other support software can be updated to support that hardware.

You show an UEFI system with BIOS installs.
So system is newer than the obsolete 12.04, and should not be expected to work.
You might try a virtual install as that uses its own drivers, but I do not know about virualbox or other options.

Better question would be why 12.04 and find a solution using your 22.04 install.

Long term you should plan on converting to gpt partitioning & UEFI boot, but that will erase system, so good backups are required.

I dont know from where did you get that the machine supports UEFI, the machine is about two years older than the 12.04 OS.

> **MAFoElffen said:**
> I do DEV?Testing and run across times when I need to do something that requires a specific release version, specific processor or specific arch. I simulate the sandbox and spin up a Virtual machine within it...

Just by coincidinence, My Ama-Gi Project, which the UbuntuForums 'system-info' script came from, was written with other scripts, on a distro I based on Ubuntu 12.04... So I have a 12.04 VM of it. 

Have you thought about installing QEMU/KVM with Virtual Machine Manager? That way you could create a VM, that boot from Legacy/CSM, and keep it safe from the outside world? That way, you could also, easily take VM snapshots, while you are doing your "version specif work."?

The work i have to do involves emulating another system inside 12.04, so i try to avoid emulating on two levels.
Besides i have the environment and everything already setup there, the problem is i couldn't boot with newer GRUB.

Anyway i found and fixed a bug in GRUB, i will report it to the maintainers so i guess the fix will be included in its future versions.

Thanks everyone.

---

### Post by oldfred on 2023-03-27
UEFI line 101 in report says:
> The firmware seems EFI-compatible,

---

### Post by gulsrb on 2023-03-27
Ok, so i found the bug exists only in Ubuntu's version of GRUB2 (from apt), regular GRUB2 source code is different and does not have that problem. 
 One would think that the developers really want to discourage people from running older kernel versions :)      

Here is a link to my bug report [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/2012972](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/2012972)

---

