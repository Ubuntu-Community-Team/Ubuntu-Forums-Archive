---
title: "GPG problem in update"
date: 2007-03-21
forum: Installation &amp; Upgrades
---

### Post by howardde on 2007-03-21
hi,
I've got a fresh edgy kubuntu install, and when i run sudo atp-get update i get a GPG error:

W: GPG error: [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems

Running update again gives the same problem.

How then, do i correct these problems? I don't know if it is related but i have been tying to get the flash player working, with mixed results, it works in opera (or flah is visible at least) but fails to in Konq.

Thanks for your time and any ideas,
Howard

---

### Post by chewearn on 2007-03-21
I have ubuntu edgy, on and off the gpg error pops up.  Eventually after a day or two, it went away by itself.  Two weeks ago it was the backport repo; the most recent case was the beryl repo.  Not sure what's going on.

---

### Post by howardde on 2007-03-22
cheers AstalaVista :)

---

### Post by zvacet on 2007-03-22
gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
 gpg --export --armor KEY | sudo apt-key add -



gpg --keyserver hkp://subkeys.pgp.net --recv-keys 2EBC26B60C5A2783
 gpg --export --armor 2EBC26B60C5A2783 | sudo apt-key add -

---

