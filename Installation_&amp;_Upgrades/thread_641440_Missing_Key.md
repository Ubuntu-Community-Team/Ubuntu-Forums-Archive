---
title: "Missing Key"
date: 2007-12-15
forum: Installation &amp; Upgrades
---

### Post by twodayslate on 2007-12-15
I was doing update for wine and moblock.

```
W: GPG error: http://wine.budgetdedicated.com gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
W: GPG error: http://moblock-deb.sourceforge.net gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CB53C4079072870B

```

Where does these programs go when download them?

---

### Post by twodayslate on 2007-12-17
figured it out!

---

### Post by colzz on 2008-05-15
> **twodayslate said:**
> figured it out!


Can you share your wisdom? 

I'm new to Ubuntu and I the same error with moblock.

W: GPG error: [http://moblock-deb.sourceforge.net](http://moblock-deb.sourceforge.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CB53C4079072870B

what do you have to do to fix this?

---

### Post by jre on 2008-05-16
To let apt verify the integrity of the packages you have to add my gpg key to the apt keyring (may be optional depending on your system's settings):
```
gpg --keyserver wwwkeys.eu.pgp.net --recv 9072870B
gpg --export --armor 9072870B | sudo apt-key add -
```

As usual for third party repositories you can get this information from the homepage (in this case moblock-deb.sourceforge.net).

Note that this is only a warning that the package signature could not be verified. So it's not an error, the package will be installed anyway (unless your distribution only installs verified packages).

greetings
jre

---

