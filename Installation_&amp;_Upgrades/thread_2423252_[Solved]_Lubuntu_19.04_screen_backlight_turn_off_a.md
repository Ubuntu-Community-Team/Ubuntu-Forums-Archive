---
title: "[Solved] Lubuntu 19.04 screen backlight turn off at login screen and don't turn on"
date: 2019-07-19
forum: Installation &amp; Upgrades
---

### Post by tony_p on 2019-07-19
Hi,

I just installed Lubuntu 19.04 on my asus eee pc 1215B netbook (AMD E-450 APU with Radeon HD 6320 Integrated Graphics, RAM: 4GB)

I got the issue with the live usb too, but i selected boot option "acpi=off" and I was able to complete the install. (Also tried "nomodeset", both "nomodeset & acpi=off", but it was unsuccessful)

So, now i have the lubuntu installed, but the screen turn off at login screen (before I can log in, even if I keep moving the cursor) and I can't wake up the screen (trying to switch to tty1-7 don't wake up the screen)

Someone have idea what I can do ?


edit: Corrected CPU model

---

### Post by pascua28 on 2019-07-22
What's the kernel version? And have you tried installing missing drivers?

---

### Post by tony_p on 2019-07-22
Ok, so now I have plugged the laptop to an external monitor and it works as a second (extended) screen and I can use the tty but shortcuts to switch screens mode or open terminal don't works (or maybe on the primary screen, which stay turned off). It's a bit annoying, but better than nothing for the moment.

Kernel is 5.0.0.
[S]I don't know if I have missing drivers and if there is a command for that.[/S]
[S]I will try to find a way to make this second screen the primary.[/S]


[S]edit: finally I have added acpi=off to grub boot cmd and the main monitor work. I will stay with that for the moment.[/S]
edit: So, i searched a bit more and adding ```
acpi_backlight=vendor
``` to grub boot cmd works... In fact it was just a backlight issue

This arch linux forum discussion: [Installation media 2019.02.01 does not boot on Asus EeePC 1215b]("https://bbs.archlinux.org/viewtopic.php?id=244190") and [this post]("https://bbs.archlinux.org/viewtopic.php?pid=1833467#p1833467") helped me

---

