---
title: "help with a script?"
date: 2007-08-14
forum: Installation &amp; Upgrades
---

### Post by mpgarate on 2007-08-14
im trying to make a little script or list of terminal commands to help me restore a fresh ubuntu installation to the way I like it, but I've been having a few little problems. does anyone see any outstanding problems they could help me with?

> wget [http://mikesubuntu.googlepages.com/xorg.conf](http://mikesubuntu.googlepages.com/xorg.conf)
sudo cp /etc/X11/xorg.conf /etc/X11/xorg2.conf
sudo cp xorg.conf /etc/X11/xorg.conf

sudo apt-get remove compiz-core desktop-effects
echo "deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy" | sudo tee -a /etc/apt/sources.list
gpg --keyserver subkeys.pgp.net --recv-keys 81836EBF
gpg --export --armor 81836EBF | sudo apt-key add -
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install ruby subversion build-essential compiz compiz-gnome compizconfig-settings-manager compiz-fusion-plugins-extra compiz-fusion-plugins-unofficial libcompizconfig-backend-gconf nautilus-open-terminal

wget [http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/automatix2_1.1-4.12-7.04feisty_i386.deb](http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/automatix2_1.1-4.12-7.04feisty_i386.deb)
sudo dpkg -i automatix2_1.1-4.12-7.04feisty_i386.deb

wget [http://mikesubuntu.googlepages.com/firefox-widgets-10.tar.bz2](http://mikesubuntu.googlepages.com/firefox-widgets-10.tar.bz2)
sudo tar -xf firefox-widgets-10.tar.bz2
cd firefox-widgets-1.0/
./install

sudo echo "enable restricted drivers, firefox extensions, add compiz --replace and emerald --replace to session"

---

