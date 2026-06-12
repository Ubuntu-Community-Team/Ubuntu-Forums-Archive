---
title: "Ubuntu crashes on install flashing caps and scroll lock"
date: 2010-11-25
forum: Installation &amp; Upgrades
---

### Post by cb154 on 2010-11-25
Hi,

Have a HP Proliant DL380 which had Ubuntu installed. Have not used it for about 6 months but wanted to resurrect the machine. Switched it on and it would not boot. Went through the usual boot load then would freeze with a flashing scroll and caps lock. Thought I would just re install and recreate the partions but now when I try to install Ubuntu 9 from an offical disc I get the same error. I have attached a screen shot (well photo). any help would be massively appreciated.

---

### Post by mörgæs on 2010-11-25
Hi, welcome to the forum.

Have you tried installing 10.04 or 10.10, preferably the alternate version?

Running memtest from the live CD is also worth trying.

---

### Post by cb154 on 2010-11-26
Installed last night. removed the m/board battery and cleared all the VRAM e.t.c then it installed without issue. will upgrade to 10 this weekend.

---

### Post by ozyaus1 on 2010-12-09
In my experience with this it was not hardware, it was because of the new drivers installed. 
For years I was on a stable release and when I upgraded to 10.10 hoping that latest was greatest -- it proved wrong. The PC would hang randomly mid booting, starting browser etc.

Had to boot with linux boot params irqpoll noapic apic=off to recover.

Edited the /etc/default/grub to have this
GRUB_CMDLINE_LINUX_DEFAULT=" quiet splash"
GRUB_CMDLINE_LINUX=" noapic apic=off irqpoll"

Then did a sudo update-grub and a reboot:popcorn:

---

