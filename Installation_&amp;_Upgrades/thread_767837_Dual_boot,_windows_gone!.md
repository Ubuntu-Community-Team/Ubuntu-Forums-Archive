---
title: "Dual boot, windows gone?!"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by occhiso on 2008-04-25
Hi,

I have a laptop, which had a WindowsXP and Ubuntu 7.10 dual boot setup.

I started to play around with ubuntu, and got it in a fairly bad state with video card drivers, etc. So decided to format.

I needed to keep my windows intact, just wipe the ubuntu partition and reload with Hardy.

Booted off the Hardy disk, formatted the ext3 partition and installed Hardy to it.
Now when grub loads there is no option for windows.

Can someone please explain to me how to get my windows back?

Help much appreciated, as this is kind of urgent, important information on that partition :tongue:

Thanks in advance

---

### Post by HunterThomson on 2008-04-25
Have you looked into the Super Grub CD.... That should solve your problem.

[http://www.supergrubdisk.org](http://www.supergrubdisk.org)

---

### Post by Lightstar on 2008-04-25
I lose my windows from my grub menu after every kernel update/upgrade.. all I do to fix is re-add this to the /boot/grub/menu.lst

title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

Your windows might be on a different hard drive.. so you might need to change the (hd0,0)
if my memory is still good, "hd0" means it's the first (master) hard ddrive and ",0" means it's the first partition on that drive

There's probably better info on the boards

---

### Post by HunterThomson on 2008-04-25
Owe, that is a way ez'r what to fix the problem:lolflag:

---

### Post by Terminating.proprietary on 2008-04-25
You should be able to access your ntfs partition from ubuntu....

---

### Post by occhiso on 2008-04-26
> **Lightstar said:**
> I lose my windows from my grub menu after every kernel update/upgrade.. all I do to fix is re-add this to the /boot/grub/menu.lst

title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

Your windows might be on a different hard drive.. so you might need to change the (hd0,0)
if my memory is still good, "hd0" means it's the first (master) hard ddrive and ",0" means it's the first partition on that drive

There's probably better info on the boards

Oh thanks a lot!
I actually already had that in the file, but it was (oddly) named Ubuntu - which booted windows :)

I changed the title to windows and it worked great.

Thanks very much!

---

