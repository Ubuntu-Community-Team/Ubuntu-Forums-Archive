---
title: "Package Managers Crash"
date: 2007-10-09
forum: Installation &amp; Upgrades
---

### Post by Xavieran on 2007-10-09
Whenever I start any package managers (Synaptic,Add/Remove,apt-get)
they crash. When I ran 'sudo apt-get remove avidemux' (a program I don't need anymore)
it prints this in the terminal:Reading package lists... Done
Segmentation fault (core dumped)

When I ran synaptic from the terminal synaptic starts up and then crashes.
The output from the terminal is this:
(synaptic:9350): Gtk-WARNING **: Default font does not have a family set

(synaptic:9350): Gtk-WARNING **: Default font does not have a positive size

(synaptic:9350): Gtk-WARNING **: Default font does not have a family set

(synaptic:9350): Gtk-WARNING **: Default font does not have a positive size

(synaptic:9350): Gtk-WARNING **: Default font does not have a family set

(synaptic:9350): Gtk-WARNING **: Default font does not have a positive size

(synaptic:9350): Gtk-WARNING **: Default font does not have a family set

(synaptic:9350): Gtk-WARNING **: Default font does not have a positive size

(synaptic:9350): Gtk-WARNING **: Default font does not have a family set

(synaptic:9350): Gtk-WARNING **: Default font does not have a positive size

(synaptic:9350): Gtk-WARNING **: Default font does not have a family set

(synaptic:9350): Gtk-WARNING **: Default font does not have a positive size

(synaptic:9350): Gtk-WARNING **: Default font does not have a family set

(synaptic:9350): Gtk-WARNING **: Default font does not have a positive size

(synaptic:9350): Gtk-WARNING **: Default font does not have a family set

(synaptic:9350): Gtk-WARNING **: Default font does not have a positive size

(synaptic:9350): Gtk-WARNING **: Default font does not have a family set

(synaptic:9350): Gtk-WARNING **: Default font does not have a positive size

(synaptic:9350): Gtk-WARNING **: Default font does not have a family set

(synaptic:9350): Gtk-WARNING **: Default font does not have a positive size
Segmentation fault (core dumped)

Any ideas :confused: .it's quite annoying because Gutsy will be coming out in a week or so and I want to be able to upgrade.

Thanks in advance for help I don't know which configs or files to post here so just let me know
I will be away for about a week at this Student Camp thing but I'll be looking forward to some answers when I get back.

Thanks

---

### Post by Pumalite on 2007-10-09
Have you tried:

sudo dpkg --configure -a

---

### Post by Xavieran on 2007-10-09
:) Thanks you have made my day I ran that command and it worked fine :KS:):grin:

---

### Post by Pumalite on 2007-10-10
You are welcome. Good luck.

---

