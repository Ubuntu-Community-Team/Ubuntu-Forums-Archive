---
title: "Virtualbox fills root directory"
date: 2010-04-03
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Michaelg14 on 2010-04-03
When I start Virtualbox as root to enable USB support it wants to place its virtual machine folders in the root directory.  I went from occupying 5 GB to 35 GB.  How can I tell it to use my separate home partition for its files?

---

### Post by snowpine on 2010-04-03
Run VirtualBox as a user and it will store its virtual machines in your /home. I can't think of any reason to run VB as root.

---

### Post by Michaelg14 on 2010-04-03
I run VB as root to enable USB support.  It is not enabled when run as a user.

---

### Post by cpmman on 2010-04-03
Ensure your user is in vboxusers group.
VBox - Settings - USB - Add USB with description.

---

### Post by snowpine on 2010-04-03
> **cpmman said:**
> Ensure your user is in vboxusers group.
VBox - Settings - USB - Add USB with description.

+1

[https://help.ubuntu.com/community/VirtualBox/USB](https://help.ubuntu.com/community/VirtualBox/USB)

---

### Post by Michaelg14 on 2010-04-03
After much file deleting, restoring from backup, and generally messing about with things, I finally got it to work as a user.  There are still VirtualBox files in the root folder one or more are enabling USB support I assume.  I did manage to delete the 30 GB file that represented my harddisk so my installation is again down around 5 GB.  With my VirtualBox files again in my home partition I am a happy camper.

Thanks to all who tried to help.

---

