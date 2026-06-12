---
title: "grub confusion in karmic beta"
date: 2009-10-08
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Chrigi on 2009-10-08
Hello

I'm very confused by my current grub setup on my karmic x64 beta.
I had the last alpha before the beta installed and therefore grub 2 (1.97beta3) was installed and presented itself on every boot so I could choose between karmic and win7. I then installed the "startupmanager" package which also installed "grub" but when I launched the app it detected grub2 and let me costumize it. I could always upate the list with "sudo update-grub2". Now that I've upgraded to the beta, grub 1.97beta3 still alows me to dual boot but when I want to update the list with "sudo update-grub2" it tells me grub2 is not installed... what the hell? Synaptic supports this.
and when I do "sudo update-grub" I get:
```
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.31-12-generic
Found kernel: /boot/vmlinuz-2.6.31-11-generic
Found GRUB 2: /boot/grub/core.img
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

```
but that does not help much as grub 2 ignores the menu.lst...

I'm terribly confused. How can I return to the correct setup? What's wrong? Or is everything correct?

---

### Post by st_itty on 2009-10-08
Check this thread [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275) startupmanager doesn't fully work with grub2. I had the same problems as well. 
I removed strartupmanger and reinstalled grub2 and edited /etc/default/grub file to make  changes and then ran
sudo update-grub2
It worked for me, hope if helps you as well.

---

### Post by Chrigi on 2009-10-10
Thank you. Worked perfectly fine.

---

