---
title: "Upgraded to 10.04 LTS problems"
date: 2010-08-17
forum: Installation &amp; Upgrades
---

### Post by rhossack on 2010-08-17
I'm a total idiot when it comes to linux.

Using dual boot with vista 64

I was using 9.4? and tried to upgrade to the 10.04 LTS and after the install it locks up the computer at the screen where it asks for name and password.

I notice that the lights on the keyboard are not on.

---

### Post by lechien73 on 2010-08-17
What hardware are you using?

Please could you try the following:

[LIST=1]
[*]When you see the Grub menu, press 'e' to edit the entry
[*]After the line which ends 'quiet splash' type a space and 'noapic' - without the quotes
[*]Press Ctrl-X to boot
[/LIST]

---

### Post by rhossack on 2010-08-17
> **lechien73 said:**
> What hardware are you using?
Thanks for the response ...

CPU	Intel Core 2 Quad Q8200  @ 2.33GHz	118 °F 	Yorkfield 45nm Technology

RAM  	4.0GB Dual-Channel DDR2 @ 399MHz (6-6-6-18)

Motherboard Dell Inc. 0M017G (CPU 1)

Graphics WS231 @ 1600x1200
	256MB ATI Radeon HD 3450 (Dell)

Hard Drives
	625GB SAMSUNG SAMSUNG HD642JJ ATA Device (IDE)	99 °F 	977GB Western Digital WDC WD10EAVS-55D7B1 ATA Device (IDE)	96 °F
Optical Drives
	YMAX MagicJack USB Device
	TSSTcorp DVD+-RW TS-H653F ATA Device
Audio
	Realtek High Definition Audio
> Please could you try the following:

[LIST=1]
[*]When you see the Grub menu, press 'e' to edit the entry
[*]After the line which ends 'quiet splash' type a space and 'noapic' - without the quotes
[*]Press Ctrl-X to boot
[/LIST]
Not sure what the 'Grub menu' is but I certainly will attempt to do this.

---

### Post by sydbat on 2010-08-17
OP - I have another question. How did you install Ubuntu? In it's own, separate partition? Or was it via wubi?

If you installed with wubi (as a program in Windows), from what I understand, upgrading from one version to another (in your case 9.04 to 10.04) can completely mess up Ubuntu.

If Ubuntu is in its own partition, following lechien73's instructions might help.

How did the upgrade go? Were there any error messages that popped up? Did the computer freeze at any time during the upgrade?

---

### Post by lechien73 on 2010-08-17
> **sydbat said:**
> OP - I have another question. How did you install Ubuntu? In it's own, separate partition? Or was it via wubi?

Good catch, thanks :) that could explain why he's not sure about the Grub menu.

---

### Post by rhossack on 2010-08-17
> **sydbat said:**
> OP - I have another question. How did you install Ubuntu? In it's own, separate partition? Or was it via wubi?
It's in its own partition.
> If Ubuntu is in its own partition, following lechien73's instructions might help.
It didn't ... I found the line in the grub menu and it still locks up at asking for the password menu.

The mouse and keyboard are dead.
> How did the upgrade go? Were there any error messages that popped up? Did the computer freeze at any time during the upgrade?
No .... to both messages and lockups.

---

### Post by lechien73 on 2010-08-18
Does 10.04 work ok if you boot from the Live CD, or does it still freeze?

You could try adding 'nomodeset xforcevesa' after 'quiet splash' because it could be a graphics driver issue. There have been problems with the ATI drivers.

---

### Post by rhossack on 2010-08-18
> **lechien73 said:**
> Does 10.04 work ok if you boot from the Live CD, or does it still freeze?
I don't have a live cd ... I just let it upgrade itself.  Will see about making one.
> You could try adding 'nomodeset xforcevesa' after 'quiet splash' because it could be a graphics driver issue. There have been problems with the ATI drivers.
Thanks ... will try that.

When I go to the Grub folder and open the menu I assume this is the line that needs attention?

title Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.32-24-generic root=UUID=40482AC8482ABD12 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash nomodeset xforcevesa
initrd		/boot/initrd.img-2.6.32-24-generic

---

### Post by rhossack on 2010-08-18
> **lechien73 said:**
> You could try adding 'nomodeset xforcevesa' after 'quiet splash' because it could be a graphics driver issue. There have been problems with the ATI drivers.
This worked!  I can now boot into ubuntu ... thanks

---

### Post by lechien73 on 2010-08-19
Great stuff, glad it's working for you now - if you get chance could you click on **Thread Tools** at the top right and mark the thread as [Solved], please?

Thanks

---

