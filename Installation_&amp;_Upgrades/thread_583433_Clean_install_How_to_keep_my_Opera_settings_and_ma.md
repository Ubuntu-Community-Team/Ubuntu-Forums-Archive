---
title: "Clean install: How to keep my Opera settings and mail ?"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by fede82 on 2007-10-20
Hi!

I want to make a clean Gutsy install (now using Feisty) but I need no to lose my current Opera browser mail/saved passwords/etc.
How can I do that?

In win it was enough to make a backup of Program Files/Opera and then just copy it again after the new installation, but I don`t know how would I do this in Opera.

Can you help me? Thanks a lot!!!
=)


PS: Using Opera 9.5 almost-lastest weekly

---

### Post by pbcartwright on 2007-10-20
in your home directory there are hidden folders that you don't normally see in a file browser. for kde /home/USER/.kde is where all your setup and config files are. in gnome it is /home/USER/.gnome
opera has its own folder /home/USER/.opera
all of your email and browser defaults, etc are somewhere under your home folder, so if you backup your entire /home directory, you will save most important settings.
if you have another drive, I would suggest using rsync to backup your home folder. I use a MyBook 500Gb external USB drive ($110 ) to backup everything.

---

