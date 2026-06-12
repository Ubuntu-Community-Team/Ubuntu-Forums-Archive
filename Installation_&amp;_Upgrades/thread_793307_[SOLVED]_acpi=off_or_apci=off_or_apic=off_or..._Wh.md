---
title: "[SOLVED] acpi=off or apci=off or apic=off or...? What the...?"
date: 2008-05-13
forum: Installation &amp; Upgrades
---

### Post by Mike Brennan on 2008-05-13
There seems to be quite a bit of confused advice floating about. I hope someone knowledgeable can clear this up.

Many people have problems with booting from Live CDs, and the advice on how to clear it up almost always involves adding a parameter to boot options. I'm new to this, and I don't really understand what this is all about. But matters are made worse by the fact that the advice is inconsistent. I've seen each of the following variants offered as advice:

   apci=off
   acpi=off
   apic=off
   acip=off

So what gives? Obviously, there is some confusion, here. Which of these is correct?

---

### Post by Pumalite on 2008-05-13
Here are some guides and the most common parameters used:
                                                                                                                                                                                                                                                                                                                                                                                                                                    [http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO.html#toc1](http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO.html#toc1)
[http://d-i.alioth.debian.org/manual/en.i386/ch05s02.html](http://d-i.alioth.debian.org/manual/en.i386/ch05s02.html)
[http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html](http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html)

[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html)
[http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html](http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html)
[http://www.knoppix.net/wiki/Cheat_Codes](http://www.knoppix.net/wiki/Cheat_Codes)
[http://www.knoppix.net/wiki/Kernel-parameters-2.6.11](http://www.knoppix.net/wiki/Kernel-parameters-2.6.11)
noapic nolapic acpi=off pci=noacpi irqpoll pnpbios=off vga=0x317

---

### Post by bobnutfield on 2008-05-13
> **Mike Brennan said:**
> There seems to be quite a bit of confused advice floating about. I hope someone knowledgeable can clear this up.

Many people have problems with booting from Live CDs, and the advice on how to clear it up almost always involves adding a parameter to boot options. I'm new to this, and I don't really understand what this is all about. But matters are made worse by the fact that the advice is inconsistent. I've seen each of the following variants offered as advice:

   apci=off
   acpi=off
   apic=off
   acip=off

So what gives? Obviously, there is some confusion, here. Which of these is correct?

acpi=off  is what you are looking for

Bob

---

### Post by cyberbill on 2008-05-13
Just bad spellers. ;)
[http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface](http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface)

acpi=off

-cb

---

### Post by Pumalite on 2008-05-13
Something about APIC:
[http://en.wikipedia.org/wiki/Advanced_Programmable_Interrupt_Controller](http://en.wikipedia.org/wiki/Advanced_Programmable_Interrupt_Controller)

---

### Post by Mike Brennan on 2008-05-13
Wow. Those were fast responses.

Thanks!

---

### Post by eleison on 2009-05-02
As a note, you might not need to entirely disable ACPI. Try using pci=noacpi to disable pci scanning while maintaining all the other benefits of apci (such as Hyperthreading). For more info, see the following page: [https://wiki.ubuntu.com/DebuggingACPI](https://wiki.ubuntu.com/DebuggingACPI)

---

