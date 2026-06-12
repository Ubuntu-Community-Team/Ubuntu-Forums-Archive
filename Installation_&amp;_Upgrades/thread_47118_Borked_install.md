---
title: "Borked install"
date: 2005-07-07
forum: Installation &amp; Upgrades
---

### Post by naelphin on 2005-07-07
I got the install CD, and tried to install it. I was confused by the "select kernel" screen, and I selected the third option (the one with numbers) I am guess I picked the wrong thing, as it is very broken now.

When I try using sudo, I put in the PW, and it spits out "User is not on the sudoers list" I'd add it to the file, but I'd need to be root to do that, which is rather hard without sudo...

---

### Post by henriette_holm on 2005-07-07
Have you tried just rebooting - and picking the first choice in the boot menu?

-Henriette

---

### Post by naelphin on 2005-07-07
[QUOTE=henriette_holm]Have you tried just rebooting - and picking the first choice in the boot menu?

-Henriette[/QUOTE]
Yes I have. The same problem in the system log, that my username isn't on the sudoers list.

---

### Post by henriette_holm on 2005-07-07
I know this is crap advice but if you have an almost fresh install why not just do a new install again?

-Henriette

---

### Post by mingus on 2005-07-07
[QUOTE=naelphin]Yes I have. The same problem in the system log, that my username isn't on the sudoers list.[/QUOTE]

This should help:

[http://www.ubuntuguide.org/#allowmoresudoers](http://www.ubuntuguide.org/#allowmoresudoers)

[http://www.ubuntuforums.org/showthread.php?t=14366](http://www.ubuntuforums.org/showthread.php?t=14366)

[http://www.ubuntuguide.org/#setchangeenablerootpassword](http://www.ubuntuguide.org/#setchangeenablerootpassword)

And to understand the nuts and bolts of it:
$man sudoers
[http://www.linuxhomenetworking.com/linux-hn/addusers.htm](http://www.linuxhomenetworking.com/linux-hn/addusers.htm)

---

