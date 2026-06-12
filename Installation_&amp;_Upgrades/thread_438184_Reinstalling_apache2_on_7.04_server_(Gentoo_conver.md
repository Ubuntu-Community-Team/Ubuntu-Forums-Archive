---
title: "Reinstalling apache2 on 7.04 server (Gentoo convert)"
date: 2007-05-09
forum: Installation &amp; Upgrades
---

### Post by jmarcus on 2007-05-09
Hi,
This is my first Ubuntu production install.  Apache2 appeared to be corrupted I was getting really odd errors trying to start it so I did a apt-get remove apache2 to get rid of apache2. This did not remove any of the apache2 configuration files or binaries. I looked around and tried a few other things but I can't get /etc/apache2 recreated or /etc/init.d/apache2.  I am new to apt-get can someone give me some pointers so that I can get apache2 reinstalled?

thanks,
James

---

### Post by rizza on 2007-05-09
There are many tools that make installation and removal very easy under ubuntu here are a few I know off the top of my head.

apt-get install (package)  apt-get remove (package)(leaves conf files in etc and other places)
apt-get remove --purge (package) (clean wipe including conf files) apt-get install --reinstall (package)
apt-get clean(clean out cached packages) apt-source install (source package) (works like portage sorta setup required, you can build from source with optimitation)

You can replace apt-get with aptitude and get better dependencies control and file clean up. I think aptitude is recommended over apt-get now anyway.

In your case you may have to install apache2 then deinstall using the --purge option then do an apt-install clean and apt-get update then install apache2 again.

This should clear the apache install completely and clear out your package cache to ensure that you don't install the same deb package that may have been corrupted in some way and download/install the most upto date apache2 deb.

Hope this helps in some way. You can always do man apt-get or man aptitude for all the details on how to use these great tools.

---

