---
title: "Instillation problems for 7.10"
date: 2008-03-27
forum: Installation &amp; Upgrades
---

### Post by indikid on 2008-03-27
Hi folks, I recently decided to shift over from Windows Xp to Ubuntu. tried to cread a dual boot system. I've got XP pro, SP2 installed. My problem is, I can't install the OS from my Ubuntu CD. I get a error upon bootup. It says: 
[0.492000] Md - BIOS bug: 8254 timer not connected to IO - APIC 
[0.492000] Kernel panic - Not syncing: IO - APIC + timer doesn't work! Boot with APIC=debug and send report and try again.

I've got a AMD 64 system, ASUSTek M2N-MX SE motherboard, Nvidia chipset and a XP pro OS.

Could someone help me out please. I'm fed up with windows and like the looks of Ubuntu. Would really like to try it out - provided I get it on my system!! - Cheers and thanks a ton... :)

---

### Post by TenPlus1 on 2008-03-27
Silly question, but did you download the 64-bit version of Ubuntu iso ???

---

### Post by erginemr on 2008-03-27
Please try:
[http://ubuntuforums.org/showthread.php?t=380553](http://ubuntuforums.org/showthread.php?t=380553)

especially post #9.

---

### Post by indikid on 2008-03-29
<TenPlus1> Yes, I've downloaded the 64bit version. Doesn't seem to work. :(

---

### Post by pbpersson on 2008-03-29
you will need to get into noapic mode as described in the previous post

---

### Post by indikid on 2008-03-29
<erginemr> This seems to be helpful. But I'm not sure if I can edit the Kernel... I'm jus an intermediate pc user and not familiar with this...

---

### Post by PmDematagoda on 2008-03-29
> **indikid said:**
> <erginemr> This seems to be helpful. But I'm not sure if I can edit the Kernel... I'm jus an intermediate pc user and not familiar with this...

You are not editing the kernel, just a booting parameter for the kernel.

When you reach the Ubuntu menu press F6, once you do that you should see a line of words, add noapic to the end of that line then try booting the Live CD.

---

### Post by indikid on 2008-04-01
Hey folks, I've managed to install Ubuntu!!! :) Turned off the APIC option in the BIOS. Say, will this be a problem?

---

### Post by erginemr on 2008-04-01
> **indikid said:**
> Hey folks, I've managed to install Ubuntu!!! :) Turned off the APIC option in the BIOS. Say, will this be a problem?

Glad that you have solved your problem. :D

I don't think that it will be a problem, but by following:
[http://en.wikipedia.org/wiki/Advanced_Programmable_Interrupt_Controller](http://en.wikipedia.org/wiki/Advanced_Programmable_Interrupt_Controller)

You can also try disabling apic only for Linux by appending the kernel parameters **noapic **and **nolapic ** to the corresponding line in the file **/boot/grub/menu.lst**. I'll go into more details if you want, but I'd say nevermind if this setting in BIOS works for you.

---

