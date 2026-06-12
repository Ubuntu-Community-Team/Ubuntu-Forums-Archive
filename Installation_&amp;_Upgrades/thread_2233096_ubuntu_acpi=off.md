---
title: "ubuntu acpi=off"
date: 2014-07-06
forum: Installation &amp; Upgrades
---

### Post by alfaceor on 2014-07-06
Hi everyone

I install ubuntu 14.04 LTS amd64 in my [laptop computer ]("http://www.asus.com/Notebooks_Ultrabooks/G60Jx/HelpDesk_Download/") (with latest BIOS update 208), but before install the only option that let me boot the live cd was the acpi=off. When i finished the installation i realize that ubuntu recognize just 1 of the 4 cores of my processor (windows recognize the 4). Also the touchpad and the "fn" keys doesn't work either. By the way, the screen resolution doesn't work but i solved the problem with the drivers.

After the installation i try to debug the acpi using the reference in the ubuntu wiki [here]("https://wiki.ubuntu.com/DebuggingACPI").

I left here some information about my system.

```
alfaceor@rolandito:~$ uname -a
Linux rolandito 3.13.0-29-generic #53-Ubuntu SMP Wed Jun 4 21:00:20 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

```

```
alfaceor@rolandito:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.13.0-29-generic root=UUID=9f7542a5-7d1c-4986-9470-677df22ce97d ro acpi=off quiet splash vt.handoff=7

```



So the complete 
 **dmesg** is [here]("http://paste.ubuntu.com/7755927/"), 
 **lspci** is [here]("http://paste.ubuntu.com/7755944/") and 
 **dmidecode** is [here]("http://paste.ubuntu.com/7755953/")

There is no /proc/acpi, thanks in advance for any help. I really desperate to solve the problem, i really need my cores!!

---

### Post by slooksterpsv on 2014-07-10
Try adding:
noapic

Not acpi its apic like a pic.
This is a common issue.

---

