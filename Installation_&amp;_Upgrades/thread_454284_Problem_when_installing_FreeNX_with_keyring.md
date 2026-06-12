---
title: "Problem when installing FreeNX with keyring"
date: 2007-05-25
forum: Installation &amp; Upgrades
---

### Post by JGuest on 2007-05-25
I was trying to install FreeNX and was following these instructions:

# Add the "seveas" repository, which contains the FreeNX packages, by editing /etc/apt/sources.list and adding the line:

deb free.linux.hp.com/~brett/seveas/freenx/ breezy-seveas freenx

# Add the GNU Privacy Guard (GnuPG) key for the "seveas" repository to your GnuPG keyring:

gpg --keyserver subkeys.pgp.net --recv-keys 1135D466
gpg --export --armor 1135D466 | sudo apt-key add -

# Retrieve the list of packages from the newly added "seveas" repository:

sudo apt-get update



After the gpg I can't do anything under ap-get, all i receive is errors:

[http://pastebin.ca/509600](http://pastebin.ca/509600)


I need to get this fixed! Please help me!!!

Thanks,
UbuntuNoooooby

---

