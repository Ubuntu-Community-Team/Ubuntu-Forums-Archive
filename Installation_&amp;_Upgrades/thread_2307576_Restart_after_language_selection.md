---
title: "Restart after language selection"
date: 2015-12-26
forum: Installation &amp; Upgrades
---

### Post by bikrus on 2015-12-26
Hi!

Can not install ubuntu 14-04-3. After language selection in few seconds just reboot. I tried ubuntu 14_04_3 server and xubuntu 14_04_3.

---

### Post by grahammechanical on 2015-12-26
We cannot help unless you give us information about the hardware specification of that machine & whether it has another OS pre-installed. For all we know you might be trying to run a 64bit Ubuntu live session on a 32 bit CPU. Which most definitely will not work.

64 bit versions of Ubuntu have amd64 as part of the name. 32 bit versions of Ubuntu have i386 as part of the name.

Regards.

---

### Post by bikrus on 2015-12-26
Oh... Sorry...

Q: hardware specification of that machine:

ubuntu@xxx:~$ lspci
00:00.0 Host bridge: NVIDIA Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: NVIDIA Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: NVIDIA Corporation MCP79 LPC Bridge (rev b3)
00:03.1 RAM memory: NVIDIA Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: NVIDIA Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: NVIDIA Corporation MCP79 Memory Controller (rev b1)
00:03.5 Co-processor: NVIDIA Corporation MCP79 Co-processor (rev b1)
00:04.0 USB controller: NVIDIA Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB controller: NVIDIA Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: NVIDIA Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: NVIDIA Corporation MCP79 PCI Bridge (rev b1)
00:0a.0 Ethernet controller: NVIDIA Corporation MCP79 Ethernet (rev b1)
00:0b.0 SATA controller: NVIDIA Corporation MCP79 AHCI Controller (rev b1)
00:0c.0 PCI bridge: NVIDIA Corporation MCP79 PCI Express Bridge (rev b1)
00:10.0 PCI bridge: NVIDIA Corporation MCP79 PCI Express Bridge (rev b1)
01:00.0 VGA compatible controller: NVIDIA Corporation ION VGA (rev b1)

Q: whether it has another OS pre-installed

I have installed Xubuntu 12.04. But I don't remember, how I installed it. There was same problems... (

About 32|64... Thanks - I know, my system works on 32 bit. I understand it and do appreciate install.

---

### Post by bikrus on 2015-12-30
Hi, everyone!

1. How to make thread [SOLVED]?
2. In short: problem solved. Reason: broken memory (RAM) modules.
In details. I tried next:
2.1. ubuntu server 14.04.3, xubuntu desktop 14.04.3, mini iso 14.04.3. Even xubuntu 15.10. All variants (i386, x64)
2.2. Startup disk creator and Unetbootin.
2.3. Mostly all reasonable options (F6) in ubuntu install menu.
2.4. Install from "try xubuntu session".
Then I tried to check memory (RAM) from xubuntu install menu. Even it was 4.20 (as I remember) and many forums tell that it is a little buggy - it show me a lot of errors. Thanks to my friends - they owe me for some time memory module. And surprise - installation of Xubuntu Desktop 14.04.3 x64 went flawlessly and fast. 

So. Thank you everybody for possible support. Problem solved. Maybe, this answer will help anybody in the world.

---

