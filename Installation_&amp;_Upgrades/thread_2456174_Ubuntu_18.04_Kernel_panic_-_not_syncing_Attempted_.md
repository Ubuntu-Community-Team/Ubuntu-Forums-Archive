---
title: "Ubuntu 18.04 Kernel panic - not syncing: Attempted to kill init!"
date: 2021-01-05
forum: Installation &amp; Upgrades
---

### Post by Karl_Ritson on 2021-01-05
I run Ubuntu 18.04. Today I attempted to install a linux driver for a HP printer M28w. I had to make a .run file executable and then execute it, which I did. It failed to install due to the dpgk folder being read only. I attempted, unsuccessfully, to fix this and long story short - I cannot get my system running. I'm writing this from my work computer because I cannot boot my Linux machine. I can get into the GRUB menu but no matter which kernel I choose, I get a message, the first few lines which are:

```
[   0.004489] do_IRQ: 1.55 No irq handler for vector
[   0.004489] do_IRQ: 2.55 No irq handler for vector
[   0.004489] do_IRQ: 3.55 No irq handler for vector
/dev/sda2: clean, 457411/45285376 files, 18485465/181124608 blocks
**** stack smashing detected ***: <unknown> terminated
[    4.87547] Kernel panic - not syncing: attempted to kill init! exitcode=0x0000000b
[    4.87585] CPU: 0 PID: 1 Comm: init Not tainted 5.4.0-48-generic #52~18.04.1-Ubuntu
[    4.87619] Hardware name: TOSHIBA Satellite L70D-A/Pumori, BIOS 1.30 09/06/2013
[    4.87651] Call Trace:
...

```

There is no prompt and it stays like this until I hold the power button down.
I have a CD-ROM of Ubuntu 14 which I can use to get Ubuntu 14 running but I am unable to get Boot repair as its not supported on Ubuntu 14.
I have no idea what to do next.
I am grateful for any help

---

### Post by CelticWarrior on 2021-01-06
Boot Repair is not for such situations.

What exactly did you do just prior to that error?

---

