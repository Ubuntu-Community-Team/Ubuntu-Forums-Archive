---
title: "disable USB drive for guest acc."
date: 2015-03-07
forum: MINT
---

### Post by flex567 on 2015-03-07
Is it possible to disable all USB drives for non-admin(guest)  user accounts? I have linux mint 17.1 ?

---

### Post by UltimateCat on 2015-03-07
You could restrict that user from belonging to a certain group.

For example on my Mint 17 my user has privileges to the following groups.

```

adm cdrom sudo dip plugdev lpadmin sambashare

``` 

If I'm not mistaken you would just not give the user privileges to the plugdev (think that's usb) and that way a guest wouldn't be able to use the usb ports.

[http://forums.linuxmint.com/viewtopic.php?f=90&t=44710](http://forums.linuxmint.com/viewtopic.php?f=90&t=44710)

[http://linux.die.net/man/1/chmod](http://linux.die.net/man/1/chmod)

---

### Post by flex567 on 2015-03-08
when I type this in terminal I get: 
adm: command not found

---

### Post by Holger_Gehrke on 2015-03-08
That was no command, it was the output of one, the 'groups' command specifically. It lists the groups a user is a member of. So to remove the user 'guest' from the 'plugdev' group, you'd get his current list of group memberships with
```

groups guest

```
and then change the user with usermod
```

usermod guest -G "replace this with a comma separated list of groups 'guest' is part of"

```

---

### Post by coffeecat on 2015-03-08
*Thread moved to **Mint** sub-forum.*

---

### Post by flex567 on 2015-03-08
when I type: groups guest 

I get: guest : guest nopasswdlogin

---

