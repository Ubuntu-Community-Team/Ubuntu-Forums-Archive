---
title: "Hardy livecd bootup fails"
date: 2008-07-21
forum: Installation &amp; Upgrades
---

### Post by vishnumrao on 2008-07-21
I am trying to install Hardy on a friends 10 year old machine with a AMD K6 processor with 392 MB of RAM, and a 64 MB SIS 6326 graphics card.

When I bootup using the Hardy Heron livecd, Xserver fails. It takes me to a failsafe Xserver. I chose the lowest screen resolution and tried to proceed. After that the machine hangs and cdrom stops spinning. I tried using booting up in the failsafe graphics mode. Same result.

Then I tried booting up with the Gutsy Gibbon livecd. Booted up perfect. Detected my graphics card and monitor correctly and setup the right screen resolution.


```
ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: ALi Corporation M1541 (rev 04)
00:01.0 PCI bridge: ALi Corporation M1541 PCI to AGP Controller (rev 04)
00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:03.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:07.0 ISA bridge: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+] (rev c3)
00:0a.0 Ethernet controller: D-Link System Inc RTL8139 Ethernet (rev 10)
00:0b.0 USB Controller: OPTi Inc. 82C861 (rev 10)
00:0f.0 IDE interface: ALi Corporation M5229 IDE (rev c1)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 86C326 5598/6326 (rev 0b)
ubuntu@ubuntu:~$ 
```


Any ideas why this could be happening? Any fixes? 

Vishnu Rao.

---

### Post by Partyboi2 on 2008-07-22
You could try installing using the [[COLOR=Blue]alternate cd [/COLOR]]("http://releases.ubuntu.com/8.04.1/")which is a text base installer.

---

