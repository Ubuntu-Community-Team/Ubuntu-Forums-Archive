---
title: "Getting a preseed file by installing manually, collecting install options?"
date: 2012-10-07
forum: Installation &amp; Upgrades
---

### Post by yanom on 2012-10-07
So I need a preseed file for automatic installation of Ubuntu with the following options:

-Wipe and Use entire disk for installation
-Install restricted extras
-Set a given username for the default user
-Set a predefined hostname for the computer ( a string generated beforehand by me, then put into the file before I run an automated install )
-Set the default user's password to be the same as the hostname
-Set the default user to log in automatically.

The manual tells me I can install manually once, then go to the installed system, install the debconf-utils package, and run this:

```
$ debconf-get-selections --installer > file
$ debconf-get-selections >> file
```

but ```
 sudo debconf-get-selections --installer 
``` returns no output when i run it. I need to collect and edit the options I put in during installation for a preseed file.

---

### Post by yanom on 2012-10-08
bump........

---

### Post by grg3 on 2012-10-22
Maybe this will help?

[]("http://http://ubuntuforums.org/showthread.php?t=1737985")

---

