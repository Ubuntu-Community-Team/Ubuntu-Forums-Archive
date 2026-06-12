---
title: "Resetting default keyboard layout"
date: 2008-09-01
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2008-09-01
Did clean load of 8.10 only to find I am stuck with dvorak keyboard.  I can reset session, but it goes back to dvorak on reboot.  I tried changing conf file per a previous post, but wound up with some sort of rules violation:

john@john-desktop:~$ sudo edit /etc/X11/xorg.conf
[sudo] password for john: 
Warning: unknown mime-type for "/etc/X11/xorg.conf" -- using "application/octet-stream"
Error: no "edit" mailcap rules found for type "application/octet-stream"
john@john-desktop:~$ 

I have standard 101 keyboard like most other US desktop PCs.

What do I need to do to get the right keyboard layout as the default.  Please don't assume I know Unix.  I am a beginner and need step-by-step.

Thank you,

John

---

### Post by JC Cheloven on 2008-09-01
Did you gave a try to the most obvious thing? In gnome desktop:

system -> preferences -> keyboard
pick tab 'layout'
press 'add' if your keyboard is not listed to add it
tick the 'default' button for your layout

Hope this helps.

---

