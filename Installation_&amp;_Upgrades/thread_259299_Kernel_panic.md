---
title: "Kernel panic"
date: 2006-09-17
forum: Installation &amp; Upgrades
---

### Post by hallco on 2006-09-17
I am unable to boot and in recovery mode I get the following message :-
"/sbin/init: relocation error: /lib/tls/i686/cmov/libc.so.6 symbol _dl_out_of_memory,version GLIBC_PRIVATE not defined in file  ld-linux.so.2 with link time reference

Kernel panic - not syncing"

Can I correct this error from the command line by using the Knoppix rescue disc?

Thanks in advance for any help

---

### Post by wieman01 on 2006-09-17
Honestly, I am not an expert but you could try this:
> 1. Boot with Live CD
2. Mount your root partition: **sudo mount /dev/hda* /mnt** [COLOR="Red"][* = your root partition][/COLOR]
3. Edit grub: **sudo gedit /mnt/boot/grub/menu.lst**
4. Change two lines so that the system loads the previous kernel when booting:
[INDENT]a. kernel **/boot/vmlinuz-[COLOR="Blue"]2.6.15-23-386[/COLOR]** root=/dev/hda3 ro quiet splash vga = 794
b. initrd **/boot/initrd.img-[COLOR="Blue"]2.6.15-23-386[/COLOR]**[/INDENT]
5. Save the file & do a normal reboot

The idea is to load your previous kernel and wait until the Ubuntu team has fixed the kernel patch.

---

### Post by hallco on 2006-09-17
Thanks for that. However I have three kernels to boot

2.6.15 -23 -386
2.6.15 -25 -386
2.6.15 -26 -386

and I get the same error message when trying to boot each of them

---

### Post by wieman01 on 2006-09-17
Oh... I thought so. Saw another similar post this morning. I reckon that other libraries have been tempered with as well. Can't help you, sorry for that.

---

