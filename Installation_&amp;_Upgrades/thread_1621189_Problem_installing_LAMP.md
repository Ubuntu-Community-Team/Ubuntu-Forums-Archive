---
title: "Problem installing LAMP"
date: 2010-11-14
forum: Installation &amp; Upgrades
---

### Post by cboxhero on 2010-11-14
**_EDIT: FIXED IT_**
So, I downloaded LAMP and it told me to make sure PHP was working after the install.
It said to type in ```
**[FONT=arial]$sudo   vi  /var/www/info.php[/FONT]**
```When I typed it in I got this:
E325: ATTENTION
Found a swap file by the name "/var/tmp/info.php.swp"
          owned by: mr-cbox   dated: Sat Nov 13 23:04:53 2010
         file name: /var/www/info.php
          modified: YES
         user name: mr-cbox   host name: Master-M
        process ID: 9115
While opening file "/var/www/info.php"

(1) Another program may be editing the same file.
    If this is the case, be careful not to end up with two
    different instances of the same file when making changes.
    Quit, or continue with caution.

(2) An edit session for this file crashed.
    If this is the case, use ":recover" or "vim -r /var/www/info.php"
    to recover the changes (see ":help recovery").
    If you did this already, delete the swap file "/var/tmp/info.php.swp"
    to avoid this message.

What do I do about this?

---

### Post by cboxhero on 2010-11-14
The tut is here. [http://www.unixmen.com/linux-distributions/4/1239-install-lamp-with-1-command-in-ubuntu-1010-maverick-meerkat](http://www.unixmen.com/linux-distributions/4/1239-install-lamp-with-1-command-in-ubuntu-1010-maverick-meerkat)

---

