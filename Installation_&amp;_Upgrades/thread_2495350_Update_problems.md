---
title: "Update problems"
date: 2024-02-15
forum: Installation &amp; Upgrades
---

### Post by Larjk on 2024-02-15
Hi, i'm trying to update Kubuntu and its applications but it gives me the following error:

> 
E: El repositorio «[https://ppa.launchpadcontent.net/ingalex/super-boot-manager/ubuntu](https://ppa.launchpadcontent.net/ingalex/super-boot-manager/ubuntu) lunar Release» no tiene un fichero de Publicación.
W: No se puede actualizar de un repositorio como este de forma segura y por tanto está deshabilitado por omisión.
W: Vea la página de manual apt-secure(8) para los detalles sobre la creación de repositorios y la configuración de usuarios.
E: El repositorio «[https://ppa.launchpadcontent.net/n-muench/burg/ubuntu](https://ppa.launchpadcontent.net/n-muench/burg/ubuntu) lunar Release» no tiene un fichero de Publicación.
W: No se puede actualizar de un repositorio como este de forma segura y por tanto está deshabilitado por omisión.
W: Vea la página de manual apt-secure(8) para los detalles sobre la creación de repositorios y la configuración de usuarios.


E: The repository "https://ppa.launchpadcontent.net/ingalex/super-boot-manager/ubuntu lunar Release" does not have a Release file.
W: It cannot be updated from a repository like this safely and is therefore disabled by default.
W: See the apt-secure(8) man page for details on creating repositories and configuring users.
E: The repository "https://ppa.launchpadcontent.net/n-muench/burg/ubuntu lunar Release" does not have a Release file.
W: It cannot be updated from a repository like this safely and is therefore disabled by default.
W: See the apt-secure(8) man page for details on creating repositories and configuring users.

And I also get this error:

[IMG]https://imgur.com/a/V1W3ewv[/IMG]

Can someone help me?
Thanks

---

### Post by yancek on 2024-02-15
You are about a month late as support for 23.04 ended on January 25, 2024.  If you are not going to useLT releases, you need to keep up to date.  The site at the link below provides necessary information.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by deadflowr on 2024-02-15
Also,
The PPA you added for Super Boot Manager has not been used in over 590 weeks now. (10 years)
The burg PPA has not been used for less, only 9 years or so.
So when you upgrade/install a new release, do not add those PPAs.

---

### Post by Larjk on 2024-02-16
OK, thank you very much.

I have been uninstalling burg and super boot manager and I have been able to update all my applications and to the latest version of Ubuntu.

---

### Post by ActionParsnip on 2024-02-16
Here are the releases that the super-boot-manager PPA supports
[https://ppa.launchpadcontent.net/ingalex/super-boot-manager/ubuntu/dists/](https://ppa.launchpadcontent.net/ingalex/super-boot-manager/ubuntu/dists/)

---

