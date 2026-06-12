---
title: "Kernel removal"
date: 2009-11-18
forum: Installation &amp; Upgrades
---

### Post by accodata on 2009-11-18
hi

I upgrade to 9.10 yesterday morning, my sound wasn't loud, as the alsamixer wasn't installed, however I did some reading on the forum and installed the  ubuntu 9.10, Kernel 2.6.31-14-generic-pae.
When I rebooted my pc, i had to go the grub menu (i think it is called) and i had to boot a differnt kernel, as the PAE one doesn't work.
How do I remove it please, so that I don't need to do this time and time again.
Many thanks

Accodata

---

### Post by Rambar on 2009-11-19
Go to Synaptic, search for "Linux image" and delete all your non-wanted kernels. If you're asking about Grub, go to a terminal and type "sudo update-grub". That will rewrite your menu.lst. If you then want to change your default booting option, open the file and edit it (it has instructions inside).

---

### Post by accodata on 2009-11-19
Hi Thanks for that

I have done both of those, and the pae is still in the menu list, 

so I am not sure what I need to do now, thanks for your answer

---

### Post by accodata on 2009-11-19
Hi

my home folder /boot/grub     wil not allow me to change the menu.lst

how on earth do I do this PLEASE

---

### Post by audiomick on 2009-11-19
Hallo.
you have to open an editor as root, as this file belongs to root, not to you.

This should work:
Start a terminal, and type

```
sudo gedit /boot/grub/menu.lst
```

whereby sudo means "let me be root", gedit is the command to start the editor, and the rest is the path to the file.

You will be asked for a password. This is the one you log on with.
Be careful when using sudo; it gives you the power to break your system.

---

### Post by accodata on 2009-11-19
fixed it, thank you for your time

have a great day

---

