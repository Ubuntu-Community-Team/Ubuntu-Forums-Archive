---
title: "Does not reboot after Linux Kernel update to 6.2.0-26"
date: 2023-08-21
forum: Installation &amp; Upgrades
---

### Post by MAFoElffen on 2023-08-21
Since my laptop upgraded the kernel to 6.2.0-26, if I reboot, it goes to the BIOS boot menu and gets stuck in a loop. If from there I do <Cntrl><Alt><Delete> it return directly to that BIOS Boot Menu.

It I shutdown from there or from the OS, it shutdown fine. If I start there, from a cold boot, it starts fine and goes to the Grub2 Boot menu.

Is anyone else having this problem?

If so, I have started a Bug report for it: [https://bugs.launchpad.net/ubuntu/+source/linux-signed-hwe-6.2/+bug/2032136](https://bugs.launchpad.net/ubuntu/+source/linux-signed-hwe-6.2/+bug/2032136)

Feel free to join it as affected.

---

### Post by evadza on 2023-08-28
You can try F12 or F7 (Ctrl+Alt+F#) while booting . what I saw then was the boot process waiting to load App Amour with no time limits. Google how to turn App Amour off and see what happens then.

My ubuntu box has raised all four legs to the sky. (Sound of taps in background)... Written from my Mac,

---

### Post by oldfred on 2023-08-28
I upgraded kernel on laptop Dell 5310, with only Intel graphics.
It shows 6.2.0-31-generic
Secure Boot is on.
I installed original Jammy and updated to 6.2 kernel a couple of weeks ago. Have not used it until today & it updated kernel again.

My main system is my laptop with older hardware and still on 5.15 kernel.

---

### Post by #&amp;thj^% on 2023-08-28
> **oldfred said:**
> I upgraded kernel on laptop Dell 5310, with only Intel graphics.
It shows 6.2.0-31-generic
Secure Boot is on.
I installed original Jammy and updated to 6.2 kernel a couple of weeks ago. Have not used it until today & it updated kernel again.

My main system is my laptop with older hardware and still on 5.15 kernel.

Same here Lenovo legion 5
```
inxi -S
System:
  Host: lvm-lite Kernel: 6.2.0-31-generic arch: x86_64 bits: 64 Desktop: Xfce
    v: 4.18.1 Distro: Linux Lite 6.4 LTS

```
Last 6 reboots
```
last reboot | head -6 
reboot   system boot  6.2.0-31-generic Mon Aug 28 08:00   still running
reboot   system boot  6.2.0-27-generic Mon Aug 28 07:52 - 07:59  (00:06)
reboot   system boot  6.2.0-27-generic Sun Aug 27 08:53 - 18:25  (09:31)
reboot   system boot  5.15.0-79-generi Sun Aug 27 07:52 - 08:52  (00:59)
reboot   system boot  5.15.0-69-generi Sun Aug 27 07:38 - 07:51  (00:13)
reboot   system boot  5.15.0-69-generi Fri Aug 25 17:19 - 17:20  (00:00)

```

---

### Post by MAFoElffen on 2023-08-28
1fallen sent me a PM letting me know of the updated kernel. That resolved my rebooting issue.

Thank you all.

---

