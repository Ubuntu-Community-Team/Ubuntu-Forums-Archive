---
title: "Booting after install"
date: 2007-07-25
forum: Installation &amp; Upgrades
---

### Post by Tootiecat on 2007-07-25
I have recently installed Ubuntu Fiesty Fawn 7.04 on one of my old computers(I used the text based installation.); the install was successful, but when I booted from my hard drive (using the boot loader LILO) after a while of going though technological gibberish it asks me for a username and password that I had created earlier.  I imputed them correctly, but they said that the username and password are not valid. 
:confused:

---

### Post by ddrichardson on 2007-07-25
Have you tried them with the caps lock on - incase it was on when you installed

---

### Post by Tootiecat on 2007-07-26
I'm pretty sure it wasdn't on, because it would have stopped me on the username about the Caps lock.  Could you tell me how I can unistall the whole thing and start all over again since I allready tried to do that without uninstalling.:confused:

---

### Post by az on 2007-07-26
> **Tootiecat said:**
> I'm pretty sure it wasdn't on, because it would have stopped me on the username about the Caps lock.  Could you tell me how I can unistall the whole thing and start all over again since I allready tried to do that without uninstalling.:confused:

Boot into recovery mode,  That will put you into a root shell

run

passwd (user)

where (user) is the name of the user you created when you installed.  Change the password and reboot.

---

### Post by Tootiecat on 2007-07-27
How do I boot into recovery mode?

---

### Post by az on 2007-07-27
> **Tootiecat said:**
> How do I boot into recovery mode?

It's not in the lilo menu?

---

### Post by Tootiecat on 2007-07-29
I did it through the Ubuntu disk and it brought me to that page and it worked fine, exept when I booted from the hard disk it didn't work with the new password.  Could I just uninstall whatever is on my hard disk and then install it again?

---

