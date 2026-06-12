---
title: "Need help with Default System Session"
date: 2005-11-18
forum: Installation &amp; Upgrades
---

### Post by TheComebackKid on 2005-11-18
Hi.
I'm new to linux and I just installed Ubuntu and everything is working fine except for automatically when I start my laptop up Ubuntu starts Gnome. I want it to startup as a terminal(command line).
Also when I'm in gnome how can I log off and end the session and go straight to a terminal and not the logon screen.
Also KDE is not in my session choices on the logon screen.

Nick

---

### Post by az on 2005-11-19
GDM is what starts the graphical display.  If you remove the symlink to it in a runlevel, and then boot into that runlevel, you will stay in the command line

Let's customise runlevel 4

sudo rm /etc/rc4.d/S13gdm

Now add a stanza in /boot/grub/menu/list

# title         Linux Runlevel four
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro 4

(adding the 4 at the end makes you boot into that runlevel)
(Yes, use the commented-out lines, and not the ones below the ## ## End Default Options ##)

Now run
sudo update-grub
to add the stanza

and you can boot into runlevel four.

If kde is not listed in your sessions, well, Is KDE installed?

---

### Post by TheComebackKid on 2005-11-20
Oops...It aint installed maybe I should do that first.
Thanks

---

