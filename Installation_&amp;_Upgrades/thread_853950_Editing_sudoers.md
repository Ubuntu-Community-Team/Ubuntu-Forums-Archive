---
title: "Editing sudoers"
date: 2008-07-09
forum: Installation &amp; Upgrades
---

### Post by Neminath on 2008-07-09
I have a perl script which executes some privileged commands.
So use sudo for that but the script has become interactive by asking for sudo password each time; which i do not want.

I found one way to avoid this is editing sudoers file giving permission for the invoking user to execute it as root. I tried doing this by entering into that still things are not working.

My sudoers file currently reads  :

[COLOR="Orange"]# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL
neminath ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
%neminath ALL=(ALL) ALL

[/COLOR]

how do i make it work any changes to my file ?

---

### Post by iaculallad on 2008-07-09
On your terminal:

```
sudo visudo
```

That's the proper way to edit and save changes to your sudoer file.

---

### Post by Neminath on 2008-07-09
using the same only i could add the marked portion
still not working 

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults !lecture,tty_tickets,!fqdn

# User privilege specification
root ALL=(ALL) ALL
[COLOR="Blue"]neminath ALL=(ALL) ALL[/COLOR]

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
[COLOR="Blue"]%neminath ALL=(ALL) ALL[/COLOR]

---

### Post by iaculallad on 2008-07-09
Try to comment this part:

**%neminath ALL=(ALL) ALL**

on this:

> # Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
#%neminath ALL=(ALL) ALL

---

