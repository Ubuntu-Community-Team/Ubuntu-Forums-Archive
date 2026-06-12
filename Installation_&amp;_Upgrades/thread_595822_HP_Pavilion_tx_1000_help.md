---
title: "HP Pavilion tx 1000 help"
date: 2007-10-29
forum: Installation &amp; Upgrades
---

### Post by ninjalaks on 2007-10-29
Hi!

I have some problem installing Ubuntu on my laptop. The desktop won't show when I am booting the CD. My computer freeze when i am almost to the desktop.

I have a Pavilion tx 1000... Can some one help me? I am sick and tierd of using windows vista.

Thanx
Robert

PS: I suck at writing english... Sorry about that:P

---

### Post by granz on 2007-10-29
sure.... boot with a live CD (if the Ubuntu one don't work, use another) 

add ... noapic nolapic to the end of the kernel line in 'boot/grub/menu.lst'. (back-up menu.lst first)
Starts and seems to run ok now ... but NO SOUND

its what I've done with a tx1001au .....  goes fine now (but waiting for an idea what to do about the sound :-(

---

### Post by ninjalaks on 2007-10-29
Ok.

But how do you add noapic nolapic?

I have never done that. Never had a problem with Ubuntu before.

---

### Post by granz on 2007-10-29
go to    'Places'  -  computer - File System - Boot - Grub - ... and open menu.lst  
scroll down to near the bottom and find something like this (add it where you see it) in the kernel line 

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=6113cada-34b6-460a-9d4b-56c2ca198d93 ro quiet splash noapic nolapic
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

---

### Post by ninjalaks on 2007-10-29
It works :P

Ubuntu is alive :D

Thanx

I have some trouble with the wireless network and sound... :S

---

