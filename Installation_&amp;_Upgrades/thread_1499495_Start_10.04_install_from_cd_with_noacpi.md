---
title: "Start 10.04 install from cd with noacpi"
date: 2010-06-02
forum: Installation &amp; Upgrades
---

### Post by loyd86 on 2010-06-02
I am unable to install ubuntu 10.04 on my desktop.

It is a k9a2gm mobo with a AMD 9750 Phenom Quad core. Just CD and hard drive hooked up right now, integrated everything else.

The install keeps giving stack trace errors, and the elusive [https://bugs.launchpad.net/ubuntu/+bug/531027](https://bugs.launchpad.net/ubuntu/+bug/531027) "GLib - getpwuid_r(): failed due to unknown user id" error. I think that I need to try to boot the kernel with no acpi but there is no option to do that in 10.04 like there was in 9.04 Any idea how to either try and boot with noacpi, or a fix to this problem?

Thanks

---

### Post by Ken Jannot on 2010-06-10
I have the same problem with this install. How to get past it?

---

### Post by wkulecz on 2010-06-10
You need to hit a key as soon and the CD bootup puts its logo box on the screen then choose your language, and press F6 to set boot options.  Unfortunately for me, booting with noacpi meant no SATA drives are found.  I was using and IDE drive with a SATA adaptor, so I could move it to the IDE port for the install and then after I set things up to boot with acpi=oldboot I could move it back to the SATA adaptor.

Here is one place where the UUID boot and mount actually helped me, but for the rest of my multiboot setup, its been a nightmare!

---

