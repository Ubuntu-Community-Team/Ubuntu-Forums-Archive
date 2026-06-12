---
title: "eject command not working in X"
date: 2009-10-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by renkinjutsu on 2009-10-13
```
eject -T /dev/sr0
```
works perfectly fine if i type it in in a tty

but it throws back ```
/. eject -T /dev/sr0
eject: unable to open `/dev/sr0'

```
when i'm in X
funny thing is that while i'm in an X session, i can log into a tty (CTRL+ALT+F?) and type the command it works! yet when switch back to X, it doesn't work! Does X change any of the permissions?

---

### Post by taavikko on 2009-10-13
It works correctly here, and
```
devil@core7:~$ ls -l `which eject`
-rwxr-xr-x 1 root root 27744 2009-04-29 03:39 /usr/bin/eject
```

Though -T has only effect when the tray is open.
[I]With this option the drive is given a CD-ROM tray close command if it's opened, and a
            CD-ROM tray eject command if it's closed.[/I]

---

### Post by renkinjutsu on 2009-10-13
```
/. ls -l $(which eject)
-rwxr-xr-x 1 root root 27744 2009-04-28 19:39 /usr/bin/eject
/. 

```
and -T works both ways... closes it if it's opened and opens it if it's closed. same as ```
--traytoggle
```

---

### Post by taavikko on 2009-10-13
> **renkinjutsu said:**
> 
and -T works both ways... closes it if it's opened and opens it if it's closed. same as 

Didn't say it doesn't work, it's just futile to use when tray is closed, as just "eject" works.

Do you have multiple drives?
Are you sure your drives support this feature? -T
```
Not  all  devices  support  this  command,
            because it uses the above CD-ROM tray close command.
```

---

### Post by renkinjutsu on 2009-10-13
Yes, it works because it worked in the tty, just not in X
Both my drives work..

I've just added my username to the group cdrom and logged out and back in, it works now.. i'll give it a reboot to see how permanent this is.. i don't remember ever having to add myself to the group before.. and what's weird is that even when not in the 'cdrom' group, i was able to use the command in the tty screens..

Okay, it works in X now.. but still confused.. am i immune to permissions while in a console?

also, i'm using a minimal install.. it'll be helpful if anyone can show me what comes out of the `groups` command

so far, this is what i've got
```
<username> lp cdrom audio video users lpadmin admin
```

---

### Post by taavikko on 2009-10-13
> **renkinjutsu said:**
> Yes, it works because it worked in the tty, just not in X
Both my drives work..

I've just added my username to the group cdrom and logged out and back in, it works now.. i'll give it a reboot to see how permanent this is.. i don't remember ever having to add myself to the group before.. and what's weird is that even when not in the 'cdrom' group, i was able to use the command in the tty screens..

Okay, it works in X now.. but still confused.. am i immune to permissions while in a console?

```
devil@core7:~$ groups
devil adm dialout cdrom plugdev lpadmin admin sambashare
```
I haven't touched my groups never. Since they should be dynamically set.

Did you did an fresh installation or upgrade from jaunty?
Or maybe GNOME is just messing with you.

---

