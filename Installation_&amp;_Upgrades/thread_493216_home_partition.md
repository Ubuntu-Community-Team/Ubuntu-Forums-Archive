---
title: "/home partition"
date: 2007-07-05
forum: Installation &amp; Upgrades
---

### Post by Xswitch on 2007-07-05
I had to reinstall Feisty on my laptop.  The install went fine, but now when I get to the desktop, there is an icon on my desktop that is named:  **sda3**.  This is my separate partition where all of my files, programs, etc., are.  

**How do I link this back to /home so that it doesn't show on my desktop anymore?**  

When I reinstalled, I changed the user name.  **Could this have caused this?**

Thanks all...

---

### Post by az on 2007-07-05
Keeping a seperate home drive is a useless pain.

You need to add an fstab entry for your partition.  You also need to make sure the user ID is the same.  The fact that you changed your used name is not important, just the number.  Well, actually, that's for file permissions.  Some configurations take into account your user name.

---

### Post by Xswitch on 2007-07-05
Thanks az....  much appreciated...

---

