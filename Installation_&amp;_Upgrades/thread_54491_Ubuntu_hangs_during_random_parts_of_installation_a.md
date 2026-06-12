---
title: "Ubuntu hangs during random parts of installation and boot"
date: 2005-08-04
forum: Installation &amp; Upgrades
---

### Post by Chris107 on 2005-08-04
This computer is starting to annoy me with my attempts at installing Linux.

I run the Ubuntu install and it runs fine.  It installs and copies the files.  Then at random parts after the files are copied where normally you'd put in your name, username, and password, it would stop and hang there and wouldn't proceed.  I reboot and do the installation over again and this time I can put my name and password.  I set my time zone, then it starts setting up the APT.  Hangs again.  I reboot and reinstall everything again.  At this point it'll either hang again at another part or finish the installation.  After installation it tries to boot.  It says Starting Ubuntu.  Then, it starts loading a bunch of things and at random times it hangs.  I reboot, and it either hangs at a different part of boot or the same part as before.  ](*,) 

This is really getting me annoyed and I'd like any help possible.

Ubuntu Live runs just fine.  :neutral:

---

### Post by Hikaru79 on 2005-08-04
The random nature of this implies you might have some hardware problems. A few suggestions, in this order:

1. Check RAM integrity: Boot the LiveCD, but instead of choosing to boot Ubuntu at the menu, choose for it to boot 'memtest86'. This will check to make sure that your RAM isn't corrupted in some way. The randomness of your problems makes this sound fairly likely.

2. Check Installation Medium integrity: Boot the installer, but once you've entered it, choose "Go Back" at the earliest opportunity, and when you get to the menu, find something along the lines of "check CD-ROM integrity". This will check to make sure you haven't burned the ISO improperly.

3. Check hard drive integrity: This is harder to do without a working operating system. If you have a Windows install anywhere, hook up your hard drive to it and run it through partition magic. I think Knoppix-STD also has some HD-checking utilities.

If its none of those, post back here and we'll go from there.

---

### Post by Chris107 on 2005-08-14
I found out it was my hard drive that was bad.  Thanks for the help.

---

### Post by Hikaru79 on 2005-08-14
[QUOTE=Chris107]I found out it was my hard drive that was bad.  Thanks for the help.[/QUOTE]
:) Hope everything works out for you. Let us know how your install went, and ask as many questions as you'd like here! Welcome to Ubuntu! \\:D/

---

