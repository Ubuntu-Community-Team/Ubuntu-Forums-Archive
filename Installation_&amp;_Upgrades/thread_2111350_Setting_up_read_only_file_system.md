---
title: "Setting up read only file system"
date: 2013-02-01
forum: Installation &amp; Upgrades
---

### Post by johnco3 on 2013-02-01
I just installed Ubuntu 12.10 on an embedded system containing a 32GB CFast storage card for the OS.  Now that I have the install nicely setup, I was wondering if there is some sort of how to set of steps that I could go through to make the system read only (soft of like with the Live CD environment).  The reason I want this is that users should be able to power off the system without having to shutdown cleanly.  We will not need to save any persistent data to the user's home folder.

Thanks in advance

John

---

### Post by SeijiSensei on 2013-02-01
I believe everything can be read-only except /var and /tmp, but you'll need to experiment to make sure.  Only root needs to write to /var.

---

### Post by Julian_Adenauer on 2013-10-08
did you get this to work, johnco3?
I want to do exactly the same and would be happy to hear about your experiences.

---

### Post by Julian_Adenauer on 2013-10-08
Ah, I just found something that does just what we need: overlayfs.
Here's how to set this up:
[http://askubuntu.com/questions/211797/how-do-i-make-ubuntu-power-loss-proof](http://askubuntu.com/questions/211797/how-do-i-make-ubuntu-power-loss-proof)

And here is a more detailed instruction but only in German:
[http://wiki.ubuntuusers.de/Nur-Lesen_Root-Dateisystem](http://wiki.ubuntuusers.de/Nur-Lesen_Root-Dateisystem)

---

