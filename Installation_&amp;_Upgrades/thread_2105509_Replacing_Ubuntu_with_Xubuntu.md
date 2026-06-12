---
title: "Replacing Ubuntu with Xubuntu"
date: 2013-01-16
forum: Installation &amp; Upgrades
---

### Post by ben222qmz7 on 2013-01-16
I have on my computer WinXp and tried to install Lubuntu .
Now it says it is Ubuntu. I am trying next to install Xubuntu.

The present Ubuntu(Lubuntu) is defective but I can log into it.

When booting the computer and the BIOS-settings adjusted accordingly, the system however goes where I can choose either windows or Ubuntu. Not to USB-flash.

As the USB flash does not start installing Xubuntu, I am wondering if I can use some command in Ubuntu to start installation from the stick?

Any comments as to what I shöuld take into consideration?

---

### Post by The Cog on 2013-01-16
That sounds to me as though your BIOS settings are wrong, or maybe your flash stick is faulty. I say this because I think the BIOS should offer you a choice of boot from hard disk or flash stick. The choice between Windows and Ubuntu is on the hard disk, not in the BIOS. If you see a choice of Windows or Ubuntu, then the BIOS has already chosen to boot from the hard disk - either because of its configuration, or because it doesn't think the stick is bootable.

---

### Post by ben222qmz7 on 2013-01-16
So, I suppose it is not possible to start installing from Ubuntu?

Ihave to check the bios settings again.

What is the command in Ubuntu to reboot?

---

### Post by The Cog on 2013-01-16
> **ben222qmz7 said:**
> So, I suppose it is not possible to start installing from Ubuntu?
I don't think so.> 
What is the command in Ubuntu to reboot?
You could use "sudo init 6", or press Ctrl-Alt-F1 (gets you a tty console) then Ctrl-Alt-Delete. ALso, there must be a logoff option in the Ubuntu screen somewhere, that offers a reboot choice.

---

