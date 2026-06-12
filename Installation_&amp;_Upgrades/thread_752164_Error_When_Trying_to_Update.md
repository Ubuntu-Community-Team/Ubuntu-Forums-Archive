---
title: "Error When Trying to Update"
date: 2008-04-11
forum: Installation &amp; Upgrades
---

### Post by mikeric on 2008-04-11
When I try to update im getting this error.
> W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

---

### Post by Pumalite on 2008-04-11
[http://www.medibuntu.org/repository.php](http://www.medibuntu.org/repository.php)

---

### Post by mikeric on 2008-04-11
do i need to change that to gutsy where it says fiesty?

---

### Post by Pumalite on 2008-04-11
Yes. OTOH, Medibuntu might not be up and running.

---

### Post by zvacet on 2008-04-11
[B]gpg --keyserver hkp://subkeys.pgp.net --recv-keys 2EBC26B60C5A2783
gpg --export --armor 2EBC26B60C5A2783 | sudo apt-key add -[/B]

---

