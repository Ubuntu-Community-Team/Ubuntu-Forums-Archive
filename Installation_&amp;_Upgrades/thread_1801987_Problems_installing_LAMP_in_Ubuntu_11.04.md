---
title: "Problems installing LAMP in Ubuntu 11.04"
date: 2011-07-11
forum: Installation &amp; Upgrades
---

### Post by _Cathy_ on 2011-07-11
Hi there. 

I am trying to install LAMP, but am running into a few problems. 

I used this first
```
sudo apt-get install lamp-server^
```

and that works fine as far as i can see -  I get a message saying "It works" when I go to localhost in a browser. 

However, now I want to test the PHP, and it is not allowing me to save any files in /var/www/. When I try to, it just says "Permission Denied"

I know (and hope) this is probably quite simple to solve, but its stopping me from doing anything! Any advice would be really appreciated :)

---

### Post by 1 clue is enough on 2011-07-11
Change ownership permissions on this directory.

In a Terminal window type:

sudo chown yourusername /var/www
sudo chgrp yourusername /var/www

Enter your password when requested.
it should fix ur problem..now u can copy and paste ur files in that folder.

---

### Post by _Cathy_ on 2011-07-11
> **1 clue is enough said:**
> Change ownership permissions on this directory.

In a Terminal window type:

sudo chown yourusername /var/www
sudo chgrp yourusername /var/www

Enter your password when requested.
it should fix ur problem..now u can copy and paste ur files in that folder.

thanks for the reply. What exactly do those commands do?

---

### Post by 1 clue is enough on 2011-07-11
**chown**  changes the user and/or group ownership of each given file or folders.
type 'man chown'  in terminal for more....

---

