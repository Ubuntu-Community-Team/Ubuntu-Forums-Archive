---
title: "trouble upgrading."
date: 2008-01-01
forum: Installation &amp; Upgrades
---

### Post by tylerdurden15 on 2008-01-01
i am trying to upgrade form 6.10 to 7.04 but when i do it gives me an error message saying something is wrong with my network, has anyone every had a problem like this?  Also will the upgrade enhance the display?  To me the pictures that come up and videos i play are not visually as nice as when i had xp.

THANKS!

---

### Post by Pumalite on 2008-01-01
Take a look at this:
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)
You might want to try this too:
sudo sed -i 's/edgy/feisty/' /etc/apt/sources.list 

sudo apt-get update 

sudo apt-get dist-upgrade

---

### Post by tylerdurden15 on 2008-01-01
what does this do exactly?

---

### Post by Pumalite on 2008-01-01
It changes your sources from Feisty to Gutsy first and then does an upgrade.

---

### Post by tylerdurden15 on 2008-01-01
i've tried what you said and still it gives me an error message:

ailed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.bz2) Sub-process bzip2 returned an error code (2)

---

### Post by Pumalite on 2008-01-01
Check your connection and/or change your Server in System>Administration>Software Sources.

---

### Post by tylerdurden15 on 2008-01-01
i changed my server from united states to main and still came up with the same error code.  It saying to check my network settings but i am obviously connected to the internet so i do not know what the problme is.  under software souces i have every box xhecked is that okay?

---

### Post by tylerdurden15 on 2008-01-02
Still having the same problem it is not fetching any of the data it needs to be, how do i fix?

---

### Post by Pumalite on 2008-01-02
Get a new sources.list from here:
[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
And then, try again.

---

### Post by tylerdurden15 on 2008-01-02
i am new to this, i got the source list but what do i do with it?

# Automatically generated sources.list
# [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -
#
# If you don't know what to do with this file, read
# [https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

# Ubuntu supported packages
# GPG key: 437D05B5
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy main restricted 
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy universe multiverse 
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe multiverse

---

### Post by Pumalite on 2008-01-02
Just try this again:
sudo sed -i 's/edgy/feisty/' /etc/apt/sources.list

sudo apt-get update

sudo apt-get dist-upgrade
__________________
Choose a good server.

---

