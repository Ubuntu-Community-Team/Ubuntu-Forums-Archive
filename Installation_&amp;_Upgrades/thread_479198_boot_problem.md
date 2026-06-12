---
title: "boot problem"
date: 2007-06-20
forum: Installation &amp; Upgrades
---

### Post by shreynaik_2004 on 2007-06-20
Hello!
	I was really interested in Ubuntu after running it in Live CD format. I wanted install it, but the problem was that in my family, other are used to run Windows XP, so I can’t remove it. So installed it in other partition. It works fine, but problem is when I start my computer, it shows more than three options, that are Ubuntu, Windows XP, Ubuntu repair mode & one more also. What I want is only two option Windows XP & Ubuntu & 1st preference to Windows XP, since other in my family want that. Please let me know how to do it.
	I tried to edit boot file, but I can’t due access problem

---

### Post by beatbros on 2007-06-20
Hi,
if your boot manager is GRUB  you have to edit (as root or sudo) the /boot/grub/menu.lst and comment the relevant sections you don't want.

As a precaution first make a backup of this file and keep it safe.
You can paste here the contents of the file to let us to help you in editin' it.

Bye

---

