---
title: "Permissions problems"
date: 2015-05-11
forum: Installation &amp; Upgrades
---

### Post by rhyshowitt on 2015-05-11
I was having some harddrive problems, so I took my box to the local computer repair place who said they did Linux.

They copied the drive over to a new one, but in the process seem to have changed a lot of permissions over from my account to another called "Me".

Initially I couldn't access a USB drive, but with Nautilus I've changed the permissions back and that works OK.

I can't get LibreOffice to work, which is killing me right now.  I've changed the permissions there, but they're not sticking for some reason.  I've tried deleting the .config.  I've tried deleting and reinstalling LibreOffice with no luck.  There's a chance I have two versions of LibreOffice (Ubuntu + a later Debian version) but this is out of my depth so don't know how to check.

Firefox is kind of working but unstable.

Is there a way to systematically change all folders assigned to "Me" to my user account?  (On Trusty BTW.)

I'm also having problems with postgresql which seems to be getting in the way of some repairs; suspect there's a permissions issue there too.

I'd rather not do a complete reinstall as my Linux skills are not all that great, I'm worried about losing files and emails, and I live in the countryside with low-grade dongle internet which slows to not much when there's traffic on the highway.

What should I do next?

Rhys
Goulburn NSW Australia

---

### Post by dino99 on 2015-05-12
dont worry Me = your user
you can rename .gconf, .gnome2, .local and .config if you want to save your settings, they will be cleanly recreated on the next boot.

and start to clean the system: clean, autoclean, autoremove, gtkorphan ; also remove possible broken links into /etc/rc?.d folders

then if the problem persist, load the app from the terminal to see the output; it can help you to solve the issue.
and finally logs should have saved some usefull warnings/errors (dmesg, xorg.0.log, ...)

---

