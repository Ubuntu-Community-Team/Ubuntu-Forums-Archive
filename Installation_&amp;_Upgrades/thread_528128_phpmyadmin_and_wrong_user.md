---
title: "phpmyadmin and wrong user"
date: 2007-08-17
forum: Installation &amp; Upgrades
---

### Post by viniosity on 2007-08-17
I've got phpmyadmin working and I've set a root password for mysql via the command line.  When I go to my phpmyadmin screen and type in username as root and password as foo I get an error that says:

```

#1045 - Access denied for user 'www-data'@'localhost' (using password: YES)

```

Not sure why it's trying to access as www-data@localhost when I'm using root as the user.  Anyone have any ideas for me?

EDIT: Ok, looks like on 64bit Ubuntu you need to apt-get install mcrypt.

---

### Post by Howler9443 on 2007-08-18
I've got the same issue. I installed mcrypt, but I still receive the error message. Was there anything else that I may have missed?

Thanks,
Howler9443

---

### Post by viniosity on 2007-08-19
> **Howler9443 said:**
> I've got the same issue. I installed mcrypt, but I still receive the error message. Was there anything else that I may have missed?


Possible.. does your phpmyadmin directory have the same permissions as your web browser?  Maybe try to chown -R www-data:www-data your phpmyadmin directory...

---

### Post by Howler9443 on 2007-08-20
Thanks, I'll give that a shot.

---

### Post by eJamesPC on 2007-09-03
I also was having this issue:
#1045 - Access denied for user 'www-data'@'localhost'

load php5-mcrypt

I also restarted apache2 after loading, but I would guess that you don't have too...

---

