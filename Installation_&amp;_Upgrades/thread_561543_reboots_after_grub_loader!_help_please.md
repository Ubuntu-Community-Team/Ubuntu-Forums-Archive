---
title: "reboots after grub loader! help please"
date: 2007-09-27
forum: Installation &amp; Upgrades
---

### Post by working41chemy on 2007-09-27
been working on this for about two weeks now. and finally decided to post. 

specs.

tul AX series mobo
amd semperon processor 2600+ 64 bit processor
1536 MB of memory (tested)
nvidia x800 video card <-- i think this might be my issue

The problem 

with a couple different cd's the installer ran into issues reading certain blocks on the cd and would hang on these errors. so i redownloaded reburned at minimum speed and finalized the disc. this seemed to fix the issue.

then after the install Grub came up counted down and rebooted immediatly. so i rebooted and hit esc. this gave me the options 

ubuntu, kernel 2.6.20-15-generic
ubuntu, kernel 2.6.20-15-generic (recovery mode)
ubuntu, memtest86+

the first one reboots immediatly 

the second loads until "acpi: pci interrupt 0000:00:1d.0 [C] ->GSI 22 (level, low) -> IRQ 22" then reboots

the third runs the memory test and passes 

any help is much appreciated.

-Adam

---

### Post by Pumalite on 2007-09-27
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)

[http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html](http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html)

[http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO-3.html](http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO-3.html)

I'm hoping is a matter of boot parameters. I hope it helps.

---

### Post by working41chemy on 2007-09-27
thanks i'll start looking into that. anyone know which boot parameters might help me?

---

### Post by working41chemy on 2007-09-27
also, i should mention it does this when loading hardware drivers

---

### Post by Pumalite on 2007-09-27
Have you tried the usual common ones: noapic. nolapic,etc?

---

### Post by working41chemy on 2007-09-27
pumalite... i love you. after using the everday linux kernel hates acpi command I.E. acpi=off i ran into a new issue ali1535 not installed..... blah blah blah. so i researched ali1535 and it seemed to relate to the ac'97 audio onboard i disabled that in the bios and booted it up.


THANK YOU!

---

### Post by Pumalite on 2007-09-28
Glad you got it working!

---

