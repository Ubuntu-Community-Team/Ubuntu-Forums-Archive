---
title: "Installing a command line system from Desktop CD"
date: 2007-03-17
forum: Installation &amp; Upgrades
---

### Post by Venator85 on 2007-03-17
Hi everybody,
is it possible to install a command line system from the live environment of the desktop cd?

Thanks
Bye
Venator ;)

---

### Post by zvacet on 2007-03-17
Do you mean server and if you do Yes.Install LAMP.

---

### Post by Venator85 on 2007-03-17
No, I mean the option "Install a command line system" present in the boot screen of the Alternate CD. I'd like to know if I can do the same thing with the Desktop live cd (even without starting the live environment).
Thanks

---

### Post by mcduck on 2007-03-17
> **Venator85 said:**
> No, I mean the option "Install a command line system" present in the boot screen of the Alternate CD. I'd like to know if I can do the same thing with the Desktop live cd (even without starting the live environment).
Thanks

Never even seen that one. If you mean the 'install in text mode' then that's just a normal install using text-based installer program (as opposed to the one in Live CD).

If you want to make the install command-line-only in the first place, use the Server CD, in other cases you could just uninstall everything you don't want..

---

### Post by zvacet on 2007-03-17
Basicly,I answered your question."Install a command line system" as option on alternate CD is option to install server.When you install server you don´t have graphical enviroment,but you can add it  later.If you installed you system from Live CD and you want to have server just install LAMP.

---

### Post by Venator85 on 2007-03-17
> **mcduck said:**
> Never even seen that one. If you mean the 'install in text mode' then that's just a normal install using text-based installer program (as opposed to the one in Live CD).

If you want to make the install command-line-only in the first place, use the Server CD, in other cases you could just uninstall everything you don't want..

Alternate CD:
[[IMG]http://img388.imageshack.us/img388/5097/alternateno3.th.gif[/IMG]](http://img388.imageshack.us/my.php?image=alternateno3.gif)

Desktop CD:
[[IMG]http://img388.imageshack.us/img388/8934/desktopfk4.th.gif[/IMG]](http://img388.imageshack.us/my.php?image=desktopfk4.gif)

Using the Server CD is not the same thing, as the installed kernel is compiled with options suitable for server usage and _not_ for desktop usage.

Uninstalling what I don't want is not a practical way, because of the significant time it would require to exactly identify the packages to remove and the time to remove them.

Bye

---

### Post by zvacet on 2007-03-17
If I understand you corectly you don´&#359; want graphical enviroment.If I´m right 
```
sudo aptitude remove ubuntu-desktop
```
As far as I can see you have alternate CD.Try that instalation you want and you will see what you will get.

---

### Post by kerry_s on 2007-03-17
Net installer, can install any supported ubuntu environment, from server to desktop.

Edgy-> [http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/netboot/mini.iso)

Feisty-> [http://ubuntu.mirror.frontiernet.net/ubuntu/dists/feisty/main/installer-i386/20061102ubuntu14/images/netboot/mini.iso](http://ubuntu.mirror.frontiernet.net/ubuntu/dists/feisty/main/installer-i386/20061102ubuntu14/images/netboot/mini.iso)

---

