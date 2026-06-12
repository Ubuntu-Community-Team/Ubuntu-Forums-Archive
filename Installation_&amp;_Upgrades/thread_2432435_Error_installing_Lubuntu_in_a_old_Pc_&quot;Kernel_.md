---
title: "Error installing Lubuntu in a old Pc: &quot;Kernel panic - not syncing: No working init fo"
date: 2019-12-02
forum: Installation &amp; Upgrades
---

### Post by hirammioni on 2019-12-02
Hi, I tried to install Lubuntu 18.04 on a old computer that has Windows XP, since apparently the BIOS (Phoeni-Award Bios v6.00PG) did not support booting from usb or CD / DVD, on Windows XP boot I installed Plop Boot Manager , to allow me to boot from the usb ...
I restarted the computer and was able to boot from the usb with lubuntu 18.04 (desktop) that I downloaded from [https://lubuntu.me/downloads/](https://lubuntu.me/downloads/), with the .torrent in Transmission (I have another computer with Ubuntu 18.04), I selected The Spanish language (I ' m from Mexico), then it appeared in the Lubuntu logo screen, select install Lubuntu and press enter, but then some errors appeared on the screen:

[HTML]
[   14.819630] Failed to execute /init (error -2)
[   14.820393] Kernel panic - not syncing: No working inlt found. I
nit= option to kernel. See Linux Documentation/admin-guide/init.rst
.
[   14.820049] CPU: 0 PID: 1 Comm: swapper/0 Not tainted 5.0.0-23-g 
.04.1-Ubuntu
[   14.820555] Hordware name: VIA Technologies, Inc. VT8601/M6VLR,
10/25/2002
[   14.820613] Call Trace:
[   14.820737] dump_stack+0x58/0x76
[   14.820798] ? rest_init+0x70/0xa0
[   14.820872] panic+0xa8/0x246
[   14.820818] ? rest_init+0xa0/0xa0
[   14.820964] kerne1_init+0xe2/0x100
[   14.821019] ret_from_fork+0x2e/0x38
[   14.821105] Kernel Offset: 0x9000000 from 0xc1000000 (relocation
00000-0xcffeffff)
[   14.821105] ---[ end Kernel panic &#8212; not syncing: No working init
passing init= option to kernel. See Linux Documentation/admin-guide/
 guidance. ]---
_
[/HTML]

If it's any use, I give you the specifications of my computer:
it is mounted in a Alaska brand housing, when i turn on the PC, the screen show the logo of Biostar.
OS: Microsoft Windows Xp Professional (5.1 compilation 2600) (Service Pack 2)
Intel Celeron CPU
1200Mhz
1.20GHz, 248MB RAM
Maxtor brand 40GB hard drive
Display with presentation of: 1024 x 768 (16 bit) (60Hz)

---

### Post by hirammioni on 2019-12-02
I want to use this old cpu more than anything to surf the internet, study, and maybe play some game with RetroPi, nothing demanding.
I want to give it a second life if possible, or some productive use.

---

### Post by rsteinmetz70112 on 2019-12-02
If you're trying to install a 64 bit Ubuntu that cpu may not work. there are 32 bit versions of lubuntu i386 available.

---

### Post by hirammioni on 2019-12-02
I know, that's the version I try to install, Lubuntu 18.04.3 LTS i386 (desktop), I put the iso in a memory with the boot disk creator, which is installed in ubuntu

---

### Post by mörgæs on 2019-12-02
I understand your interest in old hardware. I do everything I can myself to keep old iron working but anything with a VT8601 is too old to be of any use, sorry.

---

### Post by rsteinmetz70112 on 2019-12-09
lubunti 18.04 minimum hardware requirements from Wikipedia:

>   Lubuntu 18.04 LTS included a minimum of 1 GB of RAM, although 2 GB was recommended for better performance, plus a Pentium 4, Pentium M, or AMD K8 CPU or newer.

I would try increasing RAM (if possible) or trying a distro which needs less RAM like Bodhi Linux or SparkyLinux, although they both say they need 512MB. I've tried both and they work.  PuppyLinux is out there for even lighter use but I find the available applications too restricting.

Using a live lightweight Live CD/DVD like Knoppix might shed some light on the issue.

---

### Post by CatKiller on 2019-12-09
> **hirammioni said:**
> I want to use this old cpu more than anything to surf the internet

There are still some tasks that you can do with a low RAM machine. Surfing the modern Internet isn't one of them.

Recycling that machine and replacing it with a Raspberry Pi will give you a much better machine that uses a fraction of the power, with significantly fewer headaches.

---

