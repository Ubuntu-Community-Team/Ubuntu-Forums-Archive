---
title: "What is the default webserver if I choose Nexcloud role during the installation"
date: 2022-02-18
forum: Installation &amp; Upgrades
---

### Post by teomcam on 2022-02-18
During the first installation of a new server, I choose NextCloud role and all works fine. I need to tweak a few things but cannot figure out which webserver is used. It seems the apache path does not exist.

---

### Post by MAFoElffen on 2022-02-19
I would guess that since Apache is part of the LAMP Stack that it would be Apache, with MySQL...

Because the dependencies of NextCloud are:

[LIST]
[*]PHP
[*]Apache / Nginx web server
[*]MySQL / MariaDB Database server
[/LIST]

---

### Post by SeijiSensei on 2022-02-19
Do you have an /etc/apache2 directory? That's where all the Apache configurations are stored.

---

### Post by deadflowr on 2022-02-19
as far as I know Ubuntu only ships a snap version of nextcloud's server packaging.
So look in the /snap directory.
That said here: [https://github.com/nextcloud-snap/nextcloud-snap]("https://github.com/nextcloud-snap/nextcloud-snap")


Edit:
Sorry, I meant to preface this with a "how did you install it?"
So we would know if you installed from Ubuntu or grabbed it from an outside source.

---

### Post by teomcam on 2022-02-19
> **deadflowr said:**
> as far as I know Ubuntu only ships a snap version of nextcloud's server packaging.
So look in the /snap directory.
That said here: [https://github.com/nextcloud-snap/nextcloud-snap](https://github.com/nextcloud-snap/nextcloud-snap)


Edit:
Sorry, I meant to preface this with a "how did you install it?"
So we would know if you installed from Ubuntu or grabbed it from an outside source.

Thank you, you are right, there is nextcloud folder under /snap.

---

### Post by MAFoElffen on 2022-02-19
Then, as Snap Applications include all the dependencies for that application, there would have the webserver application contained there in it's own filesystem and container.

---

