---
title: "how to automatic login (gdm 2.27.4)"
date: 2009-07-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by agel1 on 2009-07-26
for some reason i don't know GDM login manager in -karmic 9.10 alpha 3- doesn't let me login, it appears, disappear and after a minute or 2 the screen go black and i have to press the power buttom

if somebody know how to enable automatic login from the terminal let me know

the live cd works without problems, thats why i know something is wrong with GDM login manager 

thanks

---

### Post by gwenn on 2009-07-26
[http://ubuntuforums.org/showthread.php?t=513820](http://ubuntuforums.org/showthread.php?t=513820)
use 'adduser' command for adding a new user on your system
 or (another variant):
[http://lists.debian.org/debian-user/2005/11/msg00228.html](http://lists.debian.org/debian-user/2005/11/msg00228.html)

You can delete the user&#8217;s password and change the following lines in /etc/pam.d/common-auth, changing:
auth required pam_unix.so nullok_secure
to:
auth required pam_unix.so nullok

---

### Post by MacUntu on 2009-07-26
Put that in the configuration file: /etc/gdm/custom.conf
```

# GDM configuration storage

[daemon]
[b]AutomaticLoginEnable=true
AutomaticLogin=YourNameHere[/b]

[xdmcp]

[chooser]

[security]

[debug]
```

Works fine but logging out isn't possible: [https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/396489](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/396489)

---

### Post by agel1 on 2009-07-27
> **MacUntu said:**
> Put that in the configuration file: /etc/gdm/custom.conf
```

# GDM configuration storage

[daemon]
[b]AutomaticLoginEnable=true
AutomaticLogin=YourNameHere[/b]

[xdmcp]

[chooser]

[security]

[debug]
```

Works fine but logging out isn't possible: [https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/396489](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/396489)thanks, this solve it

---

### Post by mrsurb on 2009-07-27
Very helpful...

In addition, I found that ubuntuone was asking for a keyring password. The work around is to delete ~/gnome2/keyrings/login.keyring and then repopulate the keyring with no password. Be warned, though, that this will store passwords (like evolution email passwords etc) in plaintext.

---

### Post by durand on 2009-07-27
> **MacUntu said:**
> Put that in the configuration file: /etc/gdm/custom.conf
```

# GDM configuration storage

[daemon]
[b]AutomaticLoginEnable=true
AutomaticLogin=YourNameHere[/b]

[xdmcp]

[chooser]

[security]

[debug]
```

Works fine but logging out isn't possible: [https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/396489](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/396489)

Thanks!

---

