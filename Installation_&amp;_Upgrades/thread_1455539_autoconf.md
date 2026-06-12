---
title: "autoconf"
date: 2010-04-16
forum: Installation &amp; Upgrades
---

### Post by sum1nil on 2010-04-16
Hi, 
From a [bug report]("http://old.nabble.com/autoconf-2.64-%2B-shtool-%3D%3E-incorrect-ac_install_sh-td26755564.html")
"It seems that autoconf 2.64 has broken "ac_install_sh" generation when configure script needs to use shtool as install script."

I get this error when trying to use autotools to compile a program called lightfeather after running aclocal and then autoconf. The package manager says shtool is installed. Do I need another package?:confused:

> @Ubunt-001:~/usr/share/lightfeather$ ./configure
configure: error: cannot find install-sh, install.sh, or shtool in "." "./.." "./../.."

I am using Karmic.

Thanks for any help.

---

