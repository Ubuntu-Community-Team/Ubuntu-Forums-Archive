---
title: "Not able to boot any Ubuntu version higher than 8.04 LTS"
date: 2014-09-06
forum: Installation &amp; Upgrades
---

### Post by thor.fyn99 on 2014-09-06
Hello all you Ubuntu-fans.

I really hope any of you can help me. I have a really old desktop computer, from before 2006 with the following specs:

Motherboard: ASUS P4P800S SE
CPU: Intel Pentium 4 (3 GHz)
Memory: 2 x Kingston 512 MB DDR
Graphics card: Nvidia GeForce FX 5200
Hard drive(s): Maxtor 2F040L0 40 GB (Parallel ATA) + Samsung SV0643A 6 GB (Parallel ATA)
DVD drive: LiteOn DVD-RW LH-20A1L
BIOS: American Megatrends
LAN: Realtek RTL8100C
USB booting: Not supported

The problem is, I can't boot any Ubuntu versions higher than 8.04 Hardy Heron. At just 8.10, I'm having trouble. If I try to boot fx. 12.04, it boots to about halfway through, before it gets completely stuck, and I can't do anything, but hard reset.
I've checked the boot DVD's very in-depth, and they are just fine. I have also tried all the suggested boot options(acpi=off, nomodeset, etc.), NONE works! 
Is it physically impossible to boot newer versions of Ubuntu on this hardware, or am I missing something, I haven't been aware of? PLEASE ANSWER!:)

Regards, Thor

---

### Post by SuperFreak on 2014-09-06
Perhaps [Lubuntu]("http://lubuntu.net/") would be a better choice

---

### Post by thor.fyn99 on 2014-09-07
I have actually tried both Xubuntu, Lubuntu and some other distros, but none works.

---

### Post by mooreted on 2014-09-07
Debian boots on just about anything. There is a steeper learning curve to Debian, but it might be worth a try. Part of the problem might be hardware that is no longer supported in newer Linux kernels.

---

### Post by ibjsb4 on 2014-09-07
This is really dated, but I wonder if it still applies.

[http://www.linuxquestions.org/questions/ubuntu-63/ubuntu-does-not-install-on-asus-p4p800-se-493299/#post2466976](http://www.linuxquestions.org/questions/ubuntu-63/ubuntu-does-not-install-on-asus-p4p800-se-493299/#post2466976)

A few more hits here.

[https://www.google.com/search?client=ubuntu&channel=fs&q=ASUS+P4P800S+SE+linux&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=ASUS+P4P800S+SE+linux&ie=utf-8&oe=utf-8)

---

### Post by thor.fyn99 on 2014-09-07
Thank you for the links ibjsb4, but the first is a solution for the P4P800 SE mobo. I've got the P4P800**S **SE. When I try to update the BIOS via the CD wizard, it won't complete. I've spent about an hour trying to search for a new BIOS to P4P800S. No results:(

---

### Post by Vladlenin5000 on 2014-09-07
[http://www.service.asus.com/#!downloads/c1wax](http://www.service.asus.com/#!downloads/c1wax)

Copy/paste your mobo model exactly as you typed in your first post, select the OS (it doesn't matter for BIOS). This will give you some results and the latest version, albeit "beta" is the recommended one:  [COLOR=#000000][FONT=Arial]P4P800S SE Beta BIOS 1007.005[/FONT][/COLOR]

---

### Post by thor.fyn99 on 2014-09-07
That is actually my latest BIOS version, that's installed. And it's that one, which isn't able to boot any Ubuntu higher than Hardy Heron.

---

