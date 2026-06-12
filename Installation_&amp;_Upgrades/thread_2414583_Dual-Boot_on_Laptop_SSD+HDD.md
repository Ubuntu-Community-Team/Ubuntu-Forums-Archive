---
title: "Dual-Boot on Laptop SSD+HDD"
date: 2019-03-12
forum: Installation &amp; Upgrades
---

### Post by tyrz on 2019-03-12
[COLOR=#242729][FONT=Arial]Hello I have a laptop (HP-Omen) and I want to dual boot Ubuntu and Windows.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]My laptop has a 120gb SSD where Windows is installed and a 1tb HDD to store all the data. I was wondering if I could make a partition on my HDD and install Ubuntu there. So I tried with making a partition from windows of my HDD with 100gb free space and then making a bootable usb with Rufus I followed the steps to install the system, i made sure to use the free space HDD partition and I created the / (90gb) the swap (9gb) and the boot partition (500mb). Everything is installed and then ubuntu asks me to restart my laptop, so I do it and it freezes.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I power off my laptop manually and Windows boot wit no sign of Ubuntu. So I go to the BIOS and try to manually boot ubuntu, but ubuntu doesn't load.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]All I want is to have Ubuntu on the HDD partition and have GRUB shown when I power on the machine.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Can anybody help me??? Thanks[/FONT][/COLOR]

---

### Post by oldfred on 2019-03-12
See this:
[https://ubuntuforums.org/showthread.php?t=2407145](https://ubuntuforums.org/showthread.php?t=2407145)
Which says to boot with acpi off.

---

### Post by tyrz on 2019-03-12
> **oldfred said:**
> See this:
[https://ubuntuforums.org/showthread.php?t=2407145](https://ubuntuforums.org/showthread.php?t=2407145)
Which says to boot with acpi off.

Hi Thank you for your help!!!

It worked with disabling the acpi.

But now the wifi doesn't work anymore, I don't know why. In the installing part wifi was working. 

Second question, how to I make the system boot the grub instead of directly booting windows and everytime that I want to change os I have to change booting disk?

Thank you for your time and help

---

### Post by oldfred on 2019-03-12
Did you install in UEFI mode?
HP has not been dual boot friendly, but some with UEFI updates have said it works better.
If you installed in UEFI boot mode, you may be able to change boot order in UEFI. Even with UEFI updates, some have reported using efibootmgr does not work. Grub install uses efibootmgr to make grub/ubuntu first in boot order, but it does not otherwise stick. There are other workarounds, if necessary.

Also can you use a hardwired Internet connection. You may then be able to easily update wireless driver.
Otherwise run wireless script & post in Wireless sub-forum.  See sticky on before you post:
[https://ubuntuforums.org/forumdisplay.php?f=336](https://ubuntuforums.org/forumdisplay.php?f=336)

---

### Post by tyrz on 2019-03-12
> **oldfred said:**
> Did you install in UEFI mode?
HP has not been dual boot friendly, but some with UEFI updates have said it works better.
If you installed in UEFI boot mode, you may be able to change boot order in UEFI. Even with UEFI updates, some have reported using efibootmgr does not work. Grub install uses efibootmgr to make grub/ubuntu first in boot order, but it does not otherwise stick. There are other workarounds, if necessary.

Also can you use a hardwired Internet connection. You may then be able to easily update wireless driver.
Otherwise run wireless script & post in Wireless sub-forum.  See sticky on before you post:
[https://ubuntuforums.org/forumdisplay.php?f=336](https://ubuntuforums.org/forumdisplay.php?f=336)

I don't know because I am new to this. I think it's in UEFI mode. I'll post a pic of the boot options
[IMG]https://ibb.co/NCc8FJJ[/IMG]
[https://ibb.co/NCc8FJJ](https://ibb.co/NCc8FJJ)

I posted on the other section of the forum for the wifi

---

### Post by oldfred on 2019-03-12
Does Ubuntu entry work?
And can you in UEFI, not UEFI boot menu, change boot order?

---

### Post by tyrz on 2019-03-12
> **oldfred said:**
> Does Ubuntu entry work?
And can you in UEFI, not UEFI boot menu, change boot order?

Yes, that's how I manage to access ubuntu, by the boot menu.

this a pic of the boot order menu

[https://ibb.co/FVtQB2b](https://ibb.co/FVtQB2b)

---

### Post by oldfred on 2019-03-12
The arrow on OS Boot Manager has UEFI entries, can you change boot order within that?

---

### Post by tyrz on 2019-03-13
> **oldfred said:**
> The arrow on OS Boot Manager has UEFI entries, can you change boot order within that?
Yes I did it, I put the OS Boot Manager as first, but still windows boots up first

---

### Post by oldfred on 2019-03-13
You have two entries in OS Boot Manager. You make the ubuntu entry first within that. 
Your screenshot in post #5 shows two OS Boot Manager entries.
And arrow in screenshow means more entries under OS Boot Manager.

---

### Post by tyrz on 2019-03-13
> **oldfred said:**
> You have two entries in OS Boot Manager. You make the ubuntu entry first within that. 
Your screenshot in post #5 shows two OS Boot Manager entries.
And arrow in screenshow means more entries under OS Boot Manager.

Oh okay I didn't know that, but how can I make ubuntu entry first? (how can I change which entry to boot?)



Thanks

---

### Post by oldfred on 2019-03-13
I do not know your system, some you just drag since UEFI has mouse support, others have arrows, so you click on one item and use arrow to move that item up or down in boot order.

---

### Post by tyrz on 2019-03-13
> **oldfred said:**
> I do not know your system, some you just drag since UEFI has mouse support, others have arrows, so you click on one item and use arrow to move that item up or down in boot order.
oh yes i did move it Up, but I mean, how can i select the ubuntu boot loader to be first intead of the windows

---

### Post by oldfred on 2019-03-13
Some with HP have not been able to do it with efibootmgr but have said after UEFI update, then changing boot order in UEFI works to keep Ubuntu first.
If Windows has major updates it will reset to be first and if grub has major updates it should reset to be first, but may not stick.

---

### Post by tyrz on 2019-03-13
> **oldfred said:**
> Some with HP have not been able to do it with efibootmgr but have said after UEFI update, then changing boot order in UEFI works to keep Ubuntu first.
If Windows has major updates it will reset to be first and if grub has major updates it should reset to be first, but may not stick.


Perfect! I did it, just a matter of clicking enter in the OS boot loader and changing the order worked!

Thanks for your help, now I am still trying to solve the wifi thing !

---

