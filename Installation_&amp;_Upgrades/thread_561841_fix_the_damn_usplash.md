---
title: "fix the damn usplash"
date: 2007-09-28
forum: Installation &amp; Upgrades
---

### Post by skopa on 2007-09-28
come on,this problem exists for ages,many people enabling the splash option in the boot menu can't boot,FIX IT OR REMOVE IT from the reps!!!

---

### Post by inportb on 2007-10-13
Can't boot? Wow.
I had a problem with usplash not appearing, but the boot process running smoothly without display.

Then I found that usplash thought my monitor was 1280x1024 when it's really 1280x800! So I fixed that in /etc/usplash.conf and ran mkinitramfs to commit it to the boot image... and it started working perfectly.

If you're using an LCD, checking your usplash.conf just _might_ help.

---

### Post by CowzRule on 2007-10-13
> **inportb said:**
> Can't boot? Wow.
I had a problem with usplash not appearing, but the boot process running smoothly without display.

Then I found that usplash thought my monitor was 1280x1024 when it's really 1280x800! So I fixed that in /etc/usplash.conf and ran mkinitramfs to commit it to the boot image... and it started working perfectly.

If you're using an LCD, checking your usplash.conf just _might_ help.

Could you tell us what the code is to "run mkinitramfs"?
Thanks

---

### Post by italianidle on 2007-10-13
Use this command after updating the usplash.conf file.
sudo update-initramfs -u
and reboot. Now the usplash maybe appears!

---

### Post by CowzRule on 2007-10-13
> **italianidle said:**
> Use this command after updating the usplash.conf file.
sudo update-initramfs -u
and reboot. Now the usplash maybe appears!
Thanks :) Like you, I have a laptop with a screen size of 1280x800 so I would add "vga=792" at the end of the kernel line in my menu.lst file. That code makes usplash display at 1024x768.
Since I like to "show off" Ubuntu to my XP friends, I want to make sure that everything is looking and working as good as it can.

---

