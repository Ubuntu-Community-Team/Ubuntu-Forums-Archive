---
title: "Must power down before reboot."
date: 2010-02-13
forum: Installation &amp; Upgrades
---

### Post by ferulebezel on 2010-02-13
I just installed and updated 9.10.

Whenever I want to reboot I have to do a hard power down. I mean all the way down such as toggling the switch on the power supply or unplugging it.

If I don't do this the booting process gets as far as the black screen with the white ubuntu logo in the middle and then hangs.

This is the case with the hard drive installation and a live DVD booting.

My mobo is an Elitegroup X58B-A2. I've not updated the bios since I don't know how.

Is there a way to supress the graphic screens when booting so I might be able to see somewhat where it is hanging.

---

### Post by ferulebezel on 2010-02-16
Some more info.  I commented out the quite splash line in /etc/default/grub and ran update-grub to see exactly where it was hanging.  For some reason this fixed the problem.

Can someone explain this?

---

