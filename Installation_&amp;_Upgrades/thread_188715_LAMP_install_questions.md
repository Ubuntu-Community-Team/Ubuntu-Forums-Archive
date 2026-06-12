---
title: "LAMP install questions"
date: 2006-06-04
forum: Installation &amp; Upgrades
---

### Post by foxmulder on 2006-06-04
Ok, I downloaded the Ubuntu 6.06 DVD (i386)

According to what I read you should have the option to install LAMP.

1) It seems this option is not available on the DVD, is this correct?
2) Is the option also available on the regular desktop .ISO (cd) ?
3) Or only on the server .ISO?
4) Is it possible to install LAMP afterwards like with "sudo apt-get install LAMP" (or something like that)?

I want the LAMP optio, but I do need the desktop as well.

Also: how about FTP and Webmin? Are they available as well?

Thanks for the trouble to read this and answer me :-)

---

### Post by llamakc on 2006-06-04
You must download and burn the ubuntu-6.06-server-$ARCH-iso and not the Desktop one.

---

### Post by foxmulder on 2006-06-04
[QUOTE=llamakc]You must download and burn the ubuntu-6.06-server-$ARCH-iso and not the Desktop one.[/QUOTE]
Ok, and how would I install the desktop environment afterwards?

And/or is there a way to install the LAMP from the desktop version?

---

### Post by llamakc on 2006-06-04
It's just a bunch of packages that are in the repositories so yeah, you can do it from the Desktop version.

Just apt-get install apache2 mysql-server php (or whatever the actual package names are) and get to the configuration part of it.

Maybe there's a metapackage that the LAMP Install on the server ISO uses?

---

### Post by llamakc on 2006-06-04
From the server version you would just `apt-get install ubuntu-desktop`

---

### Post by foxmulder on 2006-06-04
Hey thanks! I will try this...

I wonder why they didn't make it an option with the DVD? I mean: there's more than enough room ;-)

---

