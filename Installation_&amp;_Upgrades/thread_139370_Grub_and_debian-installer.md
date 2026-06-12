---
title: "Grub and debian-installer"
date: 2006-03-03
forum: Installation &amp; Upgrades
---

### Post by macmasterxiv on 2006-03-03
Ok, I recently installed Ubuntu where the grub install failed. I eventually managed to get it nearly back to normal, but not quite. Usually when it installs normally, the menu.lst is automatically updated whenever there is a kernel update in synaptic, etc. however, mine will not do that. I have to manually run update-grub to get it to update the menu.lst. What step from the debian-installer did I forget to duplicate to make that auto-updating work?

---

### Post by Mez on 2006-03-04
it should run automatically from the kernel postinst... confused ... email [email]cjwatson@ubuntu.com[/email] if you think it's a d-i problem and he'll be able to help.

Have you tried reinsalling from scratch

---

### Post by macmasterxiv on 2006-03-04
That's the problem, I don't want to have to completely reinstall just because a link between apt and grub wasn't made. I know reinstalling will fix the problem, but I was looking for an easier way.

---

