---
title: "Installing desktop components for SPARC (Sun Ultra 10)"
date: 2006-06-18
forum: Installation &amp; Upgrades
---

### Post by pdavis466 on 2006-06-18
For my forst post, I wanted to make sure that I came off as a complete n00b, so here I go...

I have a Sun Ultra 10 that I have been running Slowlaris on for some time. I have been using Xubuntu and Good ol' Ubuntu on a number of older laptops and a couple of my servers. I am interested in getting the ultra10 running Ubuntu as a desktop workstation. I installed the server disk without a problem, but there was no option for additional packages during the install, and running apt-get for the packages I knew of for SPARC got me no results  ](*,) . So here is the question:

What apt repositories and packages do I need to add/install to get a fully functional desktop running on my UltraSPARC?

---

### Post by termdex on 2006-06-19
I apologize for getting off topic but how did you get your Ultra 10 to boot?
Are you using frame buffer or serial console? Neither works for me but I have Creator3D, btw.

I ask because I'm getting the following error on serial console while trying to boot off CD:

boot:
Allocated 8 Megs of memory at 0x40000000 for kernel
Loaded kernel version 2.6.15
Loading initial ramdisk (4821666 bytes at 0x10400000 phys, 0x40C00000 virt)...
Illegal Instruction
ok

---

### Post by pdavis466 on 2006-06-20
[QUOTE=termdex]I apologize for getting off topic but how did you get your Ultra 10 to boot?
Are you using frame buffer or serial console? Neither works for me but I have Creator3D, btw.

I ask because I'm getting the following error on serial console while trying to boot off CD:

boot:
Allocated 8 Megs of memory at 0x40000000 for kernel
Loaded kernel version 2.6.15
Loading initial ramdisk (4821666 bytes at 0x10400000 phys, 0x40C00000 virt)...
Illegal Instruction
ok[/QUOTE]
I am using the built in RGB connection. I took my Creator 3d out as I have no real need for it atm. I am also open openboot 2.25, so I don't know if that will have any affect on what you are doing...

---

