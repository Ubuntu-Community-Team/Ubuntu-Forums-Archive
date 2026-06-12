---
title: "multiple hard disks"
date: 2007-10-08
forum: Installation &amp; Upgrades
---

### Post by nricci on 2007-10-08
HI there

I'm trying Ubuntu beta 7.10 and need help to install it.

My machine have 3 hard disks. 2 windows Vista (C) and data (D) and a new drive that I installed for Linux.

the configuration is
primary ide
master -> windows vista boot
slave -> data drive

secondary ide
master -> brand new drive
slave -> cd/dvd burner

I DO NOT want to use a boot loader. I want the systems to be independent and since my computer allows me to select the boot drive with F8, I guess I&#314;l be fine.

So, I'm installing Ubuntu and on step 8 I hit Advanced.

Do I select "Install boot loader"? Do I need it?
If I select it, I believe I have to install it on hd2 (the master of the secondary ide, correct)? so that linx and windows can be isolated?

Please advise and THANK you very much in advance.

Ricci

---

### Post by shad0w_walker on 2007-10-08
You will have to install the boot loader on the Linux drive as with out it there is nothing to start Linux loading but it doesn't interfere with the other hard drives as long as you install it to the same drive as you are putting Linux on. 

Yes, hd2 would be the secondary master. It starts counting from 0 (Primary, Master) and goes on logically from there.

---

### Post by nricci on 2007-10-08
Thank you Shad0w_walker.

I'm moving ahead. Wish me luck.

---

### Post by shad0w_walker on 2007-10-08
Good luck and let us know how things go. If you hit any snags I'm sure that the forums can help you out whatever they might be.

---

### Post by nricci on 2007-10-08
Well Shad0w_walker

It did not work.

Windows Vista system and data drives are intact. No harm done.

But when I select the Linux HD to boot, grub (I guess this is the name) shows me a few options. I select the first one and get a message saying that Ubuntu can't mount a partition and the grub screen is presented again.

I have no idea how to move forward now.

Thanks

Ricci

---

### Post by logos34 on 2007-10-08
> **nricci said:**
> Well Shad0w_walker

It did not work.

Windows Vista system and data drives are intact. No harm done.

But when I select the Linux HD to boot, grub (I guess this is the name) shows me a few options. I select the first one and get a message saying that Ubuntu can't mount a partition and the grub screen is presented again.

Sounds like your menu.lst is still showing root at (hd**2**,0)--as soon as you put ubuntu hard disk first in Bios boot order it becomes (hd0).  So on the grub menu screen hit 'e' to edit the ubuntu kernel, hit 'e' again on the 'root' line and change to (hd**0**,0).  Hit enter to save and 'b' to boot.  If it works go straight to menu.lst and change 'groot' and root lines accordingly.

gksudo gedit /boot/grub/menu.lst

---

### Post by nricci on 2007-10-08
hi logos34

thanks. following your advice I was able to make it work and, at the same time, learn a little bit more how linux deals with the drives. 

thanks a lot.

system is working the way I wanted now.

---

### Post by logos34 on 2007-10-08
good to hear.  

have fun with gutsy.

---

