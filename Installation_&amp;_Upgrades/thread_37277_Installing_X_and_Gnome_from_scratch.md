---
title: "Installing X and Gnome from scratch"
date: 2005-05-26
forum: Installation &amp; Upgrades
---

### Post by p.n on 2005-05-26
I am having problems with an installation and am curretnly doing a server only install after which I will attempt to install X and Gnome.  WOuld the following work from the terminal;

sudo apt-get X

followed by
sudo apt-get Gnome

?

Regards
p.n

---

### Post by tread on 2005-05-26
apt-get ubuntu-desktop 

will do that I think, though it might pull in more packages than you need. But you can always remove those later I suppose.

---

### Post by p.n on 2005-05-26
and this will only install x and gnome, not anything else like openoffice etc?

---

### Post by tread on 2005-05-26
You can find out the names of the packages to install by visiting packages.ubuntu.com and searching there .. pretty useful site.

---

### Post by p.n on 2005-05-27
I'll have a look.  I have however found that ubuntu-desktop actually pulls in everything from xfree, gnome, mysql, totem ....  (why does ubuntu still use xfree and not xorg?).  Anyway, I'll try do start over and just try to get x and gnome up and running.

Tx

EDIT: Another question.  I have been using gentoo for quite some time and am rather new to debian's apt-get.  If I should do an emerge gnome (similar to apt-get gnome) in gentoo, it calculates all the dependencies and will pull in everything it needs to successfully install gnome, including X.  Does apt-get work the same?  ie if I just do a apt-get gnome, will it pull in X as well?

(Suppose I could find this info elsewhere easy enough, just thought I asked ;-) )

---

