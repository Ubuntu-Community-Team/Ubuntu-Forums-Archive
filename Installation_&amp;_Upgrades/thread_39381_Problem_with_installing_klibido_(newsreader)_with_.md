---
title: "Problem with installing klibido (newsreader) with deb-src"
date: 2005-06-04
forum: Installation &amp; Upgrades
---

### Post by Pietro Pizzi on 2005-06-04
Hi,

I run Hoary and i have a problem with the install of klibido.

The package isn't in the Ubuntu-repo and so i would install it with the debian-src package like it ist described on the klibido HP ([http://klibido.sourceforge.net/#_download)](http://klibido.sourceforge.net/#_download)).

First "sudo apt-get install apt-build" works,
but after "apt-build build-source klibido" i get an error:

> 
dpkg-deb: building package `klibido' in `../klibido_0.2.3-1_i386.deb'.
dpkg-deb: control directory has bad permissions 2755 (must be >=0755 and <=0775)dh_builddeb: command returned error code 512
make: *** [binary-arch] Error 1
----> Cleaning up object files <-----
dh_testdir
dh_testroot
rm -f build-stamp configure-stamp config.log config.status debian/files
Error while building klibido !
Some error occured building package


I have also checkt the fedora.rpm with alien but it doesnt start, and the debian.deb needs newer deps like the ubuntu ones.

Have anybody an idea how i can fix that?

Thanks,
Pietro

---

### Post by betrayed on 2005-06-04
[QUOTE=Pietro Pizzi]Hi,

I run Hoary and i have a problem with the install of klibido.

The package isn't in the Ubuntu-repo and so i would install it with the debian-src package like it ist described on the klibido HP ([http://klibido.sourceforge.net/#_download)](http://klibido.sourceforge.net/#_download)).

First "sudo apt-get install apt-build" works,
but after "apt-build build-source klibido" i get an error:



I have also checkt the fedora.rpm with alien but it doesnt start, and the debian.deb needs newer deps like the ubuntu ones.

Have anybody an idea how i can fix that?

Thanks,
Pietro[/QUOTE]
 apt-get install apt-build
apt-build build-source klibido
cd /var/cache/apt-build/repository

I did that just like the page said but the build fails so I went to the folder and did the build by hand.  No problems, checkinstall installed it and now I use it everyday

---

### Post by zAo on 2005-06-05
[QUOTE=betrayed]apt-get install apt-build
apt-build build-source klibido
cd /var/cache/apt-build/repository

I did that just like the page said but the build fails so I went to the folder and did the build by hand.  No problems, checkinstall installed it and now I use it everyday[/QUOTE]
Why dont you give us the commandos? Thanks

---

### Post by Pietro Pizzi on 2005-06-09
No it works! I did the following:

After the error i go up one dir, chmod it to 0775, step again in the dir, rerun the last commando.

Anybody knows why apt make the dir with the wrong permissions?

---

