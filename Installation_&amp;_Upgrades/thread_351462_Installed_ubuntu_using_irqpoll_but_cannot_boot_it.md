---
title: "Installed ubuntu using irqpoll but cannot boot it"
date: 2007-02-02
forum: Installation &amp; Upgrades
---

### Post by dryder on 2007-02-02
Hi,

After some help from this forum (thanks) I managed to get the desktop and the alternative CD's to start - using boot: irqpoll

I installed from the Desktop CD and installed grub.

When I try to start Ubuntu now, it hangs as soon as the horizontal bar shows. Eventually it goes into a text mode and I see things like "try irqpoll" and "disabling IRQ..and "nobody cared".

i am now in ubuntu via the Desktop CD again and am confused with the folder structure ... presumably I need to add "irqpoll" (at least) to the startup config file.

But ....

where is the file that gives the boot parameters please?

Any suggestions very welcome, thank you.

David
____________
(When it kept saying "nobody cared" i tried typing "tell me about it" - oddly enough nothing happened ....

---

### Post by empthollow on 2007-02-02
the file you are looking for is
```
/boot/grub/menu.lst
```
you will see some lines that start with 
```
kernel
```
go to the end of that line and add irqpoll:guitar:

---

### Post by dryder on 2007-02-02
Thanks empthollow,

However, using Places I cannot see where /boot/grub/menu.lst is. (I am currently in the CD demo mode as I cannot boot).

Places>Computer shows:
Floppy drive
CD-ROM Drive
Compact Flash Drive
Memory Stick Drive
SD/MMC Drive
Smart Media Drive
Filesystem

In Filesystem there is a /boot/ folder with only abi-2.6.17.10-generic, config-2.6.17.10-generic, memtest+86.bin, System.map-2.6.17-10-generic and vmlinuz-2.6.17-10-generic. None of these can be edited. In fact, I am not even sure this is my hard disk (IDE1 SLAVE) where I installed the system.

Many thanks for helping.
David

---

### Post by empthollow on 2007-02-03
hmm, if you cannot boot when grub displays your os options press "e" to get to edit mode, i believe you have to select a boot option to edit and then you will see a few lines of code.  one of them will start with "kernel" as mentioned in my previous post press right till you get to the end of that line and type "irqpoll" there, that will tell grub to add the kernel option. i think it will save it for future use but i'm not sure.  good luck.

---

