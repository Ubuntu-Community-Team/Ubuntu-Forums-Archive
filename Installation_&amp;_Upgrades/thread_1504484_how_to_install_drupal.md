---
title: "how to install drupal?"
date: 2010-06-08
forum: Installation &amp; Upgrades
---

### Post by mkarthik90 on 2010-06-08
hi,
   Can anyone tell me all  the  steps of how to install drupal 6.0 and start using it ?

---

### Post by lechien73 on 2010-06-08
I don't think I can do any better than point you to the instructions here:

[https://wiki.ubuntu.com/UbuntuDrupal/Setup](https://wiki.ubuntu.com/UbuntuDrupal/Setup)

---

### Post by mkarthik90 on 2010-06-09
How to obtain the root user access. because when i try to paste the file in var/www/ the root user permission is required. i dont get a paste option in that directory.

---

### Post by lechien73 on 2010-06-15
It would probably be best to unpack the file through a terminal window.

So, assuming you have saved the drupal archive to your Downloads directory:

```
cd /var/www
sudo tar -xvf ~/Downloads/drupal-6.17.tar.gz
sudo mv drupal-6.17 drupal

```
Then continue with the rest of the installation instructions.

---

### Post by leg on 2010-06-15
I have added my user to the www-data group to allow me access to the /var/www directory. There are still a couple of times you need to sudo but not much. Other than that follow the instructions and access as many tutorials as you need from the [Drupal]("http://drupal.org/") site.

---

