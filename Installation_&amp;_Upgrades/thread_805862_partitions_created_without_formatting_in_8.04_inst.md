---
title: "partitions created without formatting in 8.04 install?"
date: 2008-05-24
forum: Installation &amp; Upgrades
---

### Post by arvsr1988 on 2008-05-24
can partitioning of drives be done during the installation of ubuntu 8.04 without formatting an existing partition?? right now i have a NTFS partition with windows xp..

---

### Post by Pumalite on 2008-05-24
Get Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it.
'Shrink' XP (right click on XP), choose resize from the menu. In the new space, make 3 'New' partitions:
10 GB for '/'
1 GB for /swap (/swap=RAM in laptops)
The rest for /home.
Install Ubuntu, go Manual and choose the already prepared partitions.

---

### Post by housam on 2008-05-24
> **arvsr1988 said:**
> can partitioning of drives be done during the installation of ubuntu 8.04 without formatting an existing partition?? right now i have a NTFS partition with windows xp..
Yes the installer can do it automatically , but manually as pumalite sujested is giving you a full control on your HDD.

---

### Post by Rallg on 2008-05-24
As the above replies suggested, it is probably better to first create your partitions (using GParted) before you begin the installation process, even though the installer can do it for you.

The reason is that during installation, there are places where a new user might misunderstand the instructions. But if you create your partitions first, then require the installer to use only the partitions you specify, then it will be easier to recover from a mistake.

---

