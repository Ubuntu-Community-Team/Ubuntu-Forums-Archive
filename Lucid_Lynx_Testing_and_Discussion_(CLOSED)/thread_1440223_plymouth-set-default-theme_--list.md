---
title: "plymouth-set-default-theme --list"
date: 2010-03-27
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by grandtoubab on 2010-03-27
Hello all
According to
[http://manpages.ubuntu.com/manpages/lucid/man8/plymouth.8.html](http://manpages.ubuntu.com/manpages/lucid/man8/plymouth.8.html)

It is possible to manage plymouth theme.

But when running
```
root@ubuntu-desktop:/#  plymouth-set-default-theme --list
Le programme « plymouth-set-default-theme » n'est pas installé.  Vous pouvez l'installer en saisissant 
apt-get install plymouth
```
The system told me to install Plymouth !!!
But it is installed
```
root@ubuntu-desktop:/# locate plymouth
/bin/plymouth
/etc/alternatives/default.plymouth
/etc/init/plymouth-log.conf
/etc/init/plymouth-splash.conf
/etc/init/plymouth-stop.conf
/etc/init/plymouth.conf
/etc/init.d/plymouth
/etc/init.d/plymouth-log
/etc/init.d/plymouth-splash
/etc/init.d/plymouth-stop
/etc/rc0.d/K20plymouth
/etc/rc1.d/K20plymouth
/etc/rc2.d/S20plymouth
/etc/rc3.d/S20plymouth
/etc/rc4.d/S20plymouth
/etc/rc5.d/S20plymouth
/etc/rc6.d/K20plymouth
/lib/plymouth
/lib/plymouth/details.so
/lib/plymouth/fade-throbber.so
/lib/plymouth/label.so
/lib/plymouth/renderers
/lib/plymouth/script.so
/lib/plymouth/themes
/lib/plymouth/ubuntu-logo.png
/lib/plymouth/renderers/drm.so
/lib/plymouth/renderers/frame-buffer.so
/lib/plymouth/renderers/vga16fb.so
/lib/plymouth/themes/default.plymouth
/lib/plymouth/themes/details
/lib/plymouth/themes/fade-in
/lib/plymouth/themes/details/details.plymouth
/lib/plymouth/themes/fade-in/bullet.png
/lib/plymouth/themes/fade-in/entry.png
/lib/plymouth/themes/fade-in/fade-in.plymouth
/lib/plymouth/themes/fade-in/lock.png
/lib/plymouth/themes/fade-in/star.png
/sbin/plymouthd
/usr/share/apport/package-hooks/source_plymouth.py
/usr/share/doc/libplymouth2
/usr/share/doc/plymouth
/usr/share/doc/plymouth-theme-fade-in
/usr/share/doc/libplymouth2/changelog.Debian.gz
/usr/share/doc/libplymouth2/changelog.gz
/usr/share/doc/libplymouth2/copyright
/usr/share/doc/plymouth/README.Debian
/usr/share/doc/plymouth/changelog.Debian.gz
/usr/share/doc/plymouth/changelog.gz
/usr/share/doc/plymouth/copyright
/usr/share/doc/plymouth-theme-fade-in/changelog.Debian.gz
/usr/share/doc/plymouth-theme-fade-in/changelog.gz
/usr/share/doc/plymouth-theme-fade-in/copyright
/usr/share/initramfs-tools/hooks/plymouth
/usr/share/initramfs-tools/scripts/init-bottom/plymouth
/usr/share/initramfs-tools/scripts/init-top/plymouth
/var/cache/apt/archives/libplymouth2_0.8.1-1_i386.deb
/var/cache/apt/archives/plymouth-theme-fade-in_0.8.1-1_i386.deb
/var/cache/apt/archives/plymouth_0.8.0~-17_i386.deb
/var/cache/apt/archives/plymouth_0.8.1-1_i386.deb
/var/lib/plymouth
/var/lib/dpkg/alternatives/default.plymouth
/var/lib/dpkg/info/libplymouth2.list
/var/lib/dpkg/info/libplymouth2.md5sums
/var/lib/dpkg/info/libplymouth2.postinst
/var/lib/dpkg/info/libplymouth2.postrm
/var/lib/dpkg/info/libplymouth2.shlibs
/var/lib/dpkg/info/libplymouth2.symbols
/var/lib/dpkg/info/plymouth-theme-fade-in.list
/var/lib/dpkg/info/plymouth-theme-fade-in.md5sums
/var/lib/dpkg/info/plymouth-theme-fade-in.postinst
/var/lib/dpkg/info/plymouth-theme-fade-in.postrm
/var/lib/dpkg/info/plymouth.conffiles
/var/lib/dpkg/info/plymouth.list
/var/lib/dpkg/info/plymouth.md5sums
/var/lib/dpkg/info/plymouth.postinst
/var/lib/dpkg/info/plymouth.postrm
/var/lib/dpkg/info/plymouth.preinst
/var/lib/plymouth/boot-duration
/var/lib/plymouth/shutdown-duration
```

What's happening?? :o

---

### Post by vishalrao on 2010-03-27
i see it too. i think there are packaging bugs when they recently updated to latest upstream plymouth 0.8.1 :) it should be fixed quick enough - have patience... all good things come to those who wait!

you can ignore it and manually link your plymouth themes default.plymouth and text.plymouth in /lib/plymouth/themes folder if you know/search for the info...

---

### Post by hugmenot on 2010-03-29
Plymouth uses update-alternatives nowadays.

Use this to select the theme:

sudo update-alternatives --config default.plymouth

---

### Post by grandtoubab on 2010-03-29
```
ubuntu-desktop:~$ sudo update-alternatives --config default.plymouth

Il existe 6 choix pour l'alternative default.plymouth (qui fournit /lib/plymouth/themes/default.plymouth).

  Sélection   Chemin                                                 Priorité  État
------------------------------------------------------------
* 0            /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.plymouth   100       mode automatique
  1            /lib/plymouth/themes/fade-in/fade-in.plymouth           10        mode manuel
  2            /lib/plymouth/themes/glow/glow.plymouth                 10        mode manuel
  3            /lib/plymouth/themes/script/script.plymouth             10        mode manuel
  4            /lib/plymouth/themes/solar/solar.plymouth               10        mode manuel
  5            /lib/plymouth/themes/spinfinity/spinfinity.plymouth     10        mode manuel
  6            /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.plymouth   100       mode manuel

Appuyez sur <Entrée> pour conserver la valeur par défaut
[*] ou choisissez le numéro sélectionné :4
update-alternatives: utilisation de « /lib/plymouth/themes/solar/solar.plymouth » pour fournir « /lib/plymouth/themes/default.plymouth » (default.plymouth) en mode manuel.
```

OK Thanks

Solar is my favourite ;)

---

### Post by grandtoubab on 2010-03-29
```
ubuntu-desktop:~$ sudo update-alternatives --config default.plymouth

Il existe 6 choix pour l'alternative default.plymouth (qui fournit /lib/plymouth/themes/default.plymouth).

  Sélection   Chemin                                                 Priorité  État
------------------------------------------------------------
* 0            /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.plymouth   100       mode automatique
  1            /lib/plymouth/themes/fade-in/fade-in.plymouth           10        mode manuel
  2            /lib/plymouth/themes/glow/glow.plymouth                 10        mode manuel
  3            /lib/plymouth/themes/script/script.plymouth             10        mode manuel
  4            /lib/plymouth/themes/solar/solar.plymouth               10        mode manuel
  5            /lib/plymouth/themes/spinfinity/spinfinity.plymouth     10        mode manuel
  6            /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.plymouth   100       mode manuel

Appuyez sur <Entrée> pour conserver la valeur par défaut
[*] ou choisissez le numéro sélectionné :4
update-alternatives: utilisation de « /lib/plymouth/themes/solar/solar.plymouth » pour fournir « /lib/plymouth/themes/default.plymouth » (default.plymouth) en mode manuel.
```

OK Thanks

Solar is my favourite ;)

---

