---
title: "Kernel hangs at install--AUX port?"
date: 2008-06-03
forum: Installation &amp; Upgrades
---

### Post by Das84 on 2008-06-03
Hello,

I'm trying to install Ubuntu 8.04 on a Dell Optiplex 320 machine, but the install just hangs beyond where I select the language and where I choose if I want to try Ubuntu, install Ubuntu, do a memory test, etc.

If I choose to either install or try out Ubuntu, the kernel will load, but then go to a black screen with a blinking cursor at the top left.  When I edit the boot parameters and remove "quiet", I see that it freezes at:

[SIZE="4"][FONT="Arial"]serio: i8042 Aux port at 0x60, 0x64 irq 12[/FONT][/SIZE]

Any help would be greatly appreciated.  Also, if this question has already been answered, a link to that answer will be equally appreciated.

Thank you

---

### Post by hal8000 on 2008-06-03
when booting with the live CD press F6, and enter

irqpoll

to the end of the grub prompt.
Your error ends with irq12, its possibly an IRQ problem, irqpoll may allow you to boot, hope that helps

---

### Post by Das84 on 2008-06-03
> **hal8000 said:**
> when booting with the live CD press F6, and enter

irqpoll

to the end of the grub prompt.
Your error ends with irq12, its possibly an IRQ problem, irqpoll may allow you to boot, hope that helps

Thanks for your reply.

I tried that parameter along with every "i8042.[whatever]" parameter I can find and the son of a gun just won't go through.  I even tried disabling most of the the onboard devices in the BIOS, but no avail.

I mean Ubuntu runs so smooth on my laptop, but on the Dell...nothing.

---

