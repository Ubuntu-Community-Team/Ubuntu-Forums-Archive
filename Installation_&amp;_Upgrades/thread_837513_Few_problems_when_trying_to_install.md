---
title: "Few problems when trying to install"
date: 2008-06-22
forum: Installation &amp; Upgrades
---

### Post by Jonaruto on 2008-06-22
I have windows xp sp2 installed on my computer, and I want to install ubuntu too.
when I am trying to install I get this:

ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
ata4.00: cmd a0/00:00:00:24:00/00:00:00:00:00/a0 tag 0 pio 36 in
ata4.00: status: { DRDY }
Buffer I/O error on device fd0, logical block 0
(its repeating)

Please help, I got to install ubuntu!
Thanks in advance!

---

### Post by Pumalite on 2008-06-22
Try the Alternate CD. Or try all_generic_ide at the end of the boot line.

---

### Post by dakal on 2008-06-22
"fd0" is Linux-speak for the first floppy drive in the system (what is known as "A:" in Windows), and DRDY plus a buffer I/O error sounds to me like it is not ready. Do you by any chance not have a floppy drive installed in your system?

If you do have a floppy drive in your system, and by chance have an old floppy disk laying around somewhere, simply inserting it should make the error go away.

---

### Post by Jonaruto on 2008-06-22
> **Pumalite said:**
> Try the Alternate CD. Or try all_generic_ide at the end of the boot line.

I will try this.


> **dakal said:**
> "fd0" is Linux-speak for the first floppy drive in the system (what is known as "A:" in Windows), and DRDY plus a buffer I/O error sounds to me like it is not ready. Do you by any chance not have a floppy drive installed in your system?

If you do have a floppy drive in your system, and by chance have an old floppy disk laying around somewhere, simply inserting it should make the error go away.


I dont have a floppy drive on my pc, and dont have an old 1.
Is there a way to fix that error without needing this?

---

### Post by Pumalite on 2008-06-22
There are a few boot parameters you can try. Repost back and I'll give you some more to try.

---

### Post by Jonaruto on 2008-06-22
> **Pumalite said:**
> Try the Alternate CD. Or try all_generic_ide at the end of the boot line.

What u mean at the end of the boot line?
you mean in the menu press f6 while install is selected and add all_generic_ide before the -- in the end? 
If yes, it gave me black screen.

---

### Post by Pumalite on 2008-06-22
Try your luck:
Boot parameters
[http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO.html#toc1](http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO.html#toc1)
[http://d-i.alioth.debian.org/manual/en.i386/ch05s02.html](http://d-i.alioth.debian.org/manual/en.i386/ch05s02.html)
[http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html](http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html)

[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html)
[http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html](http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html)
[http://www.knoppix.net/wiki/Cheat_Codes](http://www.knoppix.net/wiki/Cheat_Codes)
[http://www.knoppix.net/wiki/Kernel-parameters-2.6.11](http://www.knoppix.net/wiki/Kernel-parameters-2.6.11)
noapic nolapic acpi=off  irqpoll pci=noacpi pnpbios=off vga=0x317 vga=788 vga=789 vga=791
To be tried one at the time or in different combinations until you hit the right one.

---

### Post by Jonaruto on 2008-06-22
> **Pumalite said:**
> Try your luck:
Boot parameters
[http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO.html#toc1](http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO.html#toc1)
[http://d-i.alioth.debian.org/manual/en.i386/ch05s02.html](http://d-i.alioth.debian.org/manual/en.i386/ch05s02.html)
[http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html](http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html)

[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html)
[http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html](http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html)
[http://www.knoppix.net/wiki/Cheat_Codes](http://www.knoppix.net/wiki/Cheat_Codes)
[http://www.knoppix.net/wiki/Kernel-parameters-2.6.11](http://www.knoppix.net/wiki/Kernel-parameters-2.6.11)
noapic nolapic acpi=off  irqpoll pci=noacpi pnpbios=off vga=0x317 vga=788 vga=789 vga=791
To be tried one at the time or in different combinations until you hit the right one.


where do I write this boot parameters?

---

### Post by Pumalite on 2008-06-22
[http://grumpymole.blogspot.com/2007/...arameters.html](http://grumpymole.blogspot.com/2007/...arameters.html)

---

### Post by Jonaruto on 2008-06-22
> **Pumalite said:**
> [http://grumpymole.blogspot.com/2007/...arameters.html](http://grumpymole.blogspot.com/2007/...arameters.html)

tnx, I hope I will fix it...

---

### Post by Pumalite on 2008-06-22
Good luck!

---

### Post by Jonaruto on 2008-06-23
I couldn't solve it... dunno whats that grub screen...
Any help?

---

### Post by Pumalite on 2008-06-23
What do you need to know? Did you read that link I gave you?

---

### Post by Jonaruto on 2008-06-23
> **Pumalite said:**
> What do you need to know? Did you read that link I gave you?

Yes, I read it,

[B]"Generally, this is used when you want to try a parameter change to see it is beneficial to your system. When the PC boots up, you will see the Grub countdown, which is set to 3 seconds by default. Press "Esc" to intercept this countdown and go enter a Grub menu. Then"
[/B]
I dont have any grub countdown, how do I get that?

---

### Post by Pumalite on 2008-06-23
'What u mean at the end of the boot line?
you mean in the menu press f6 while install is selected and add all_generic_ide before the -- in the end?
If yes, it gave me black screen.'
Try other combinations.

---

