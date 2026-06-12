---
title: "apt-get"
date: 2008-02-28
forum: Installation &amp; Upgrades
---

### Post by bratliff on 2008-02-28
What's with when I run apt-get I get this:
                                        GPG error: [http://dl.google.com](http://dl.google.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
W: GPG error: [http://www.debian-multimedia.org](http://www.debian-multimedia.org) sid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: You may want to run apt-get update to correct these problems

I run apt-get and get this error that says run apt-get to correct. Full circle. 

Ratliff

---

### Post by overdrank on 2008-02-28
> **bratliff said:**
> What's with when I run apt-get I get this:
                                        GPG error: [http://dl.google.com](http://dl.google.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
W: GPG error: [http://www.debian-multimedia.org](http://www.debian-multimedia.org) sid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: You may want to run apt-get update to correct these problems

I run apt-get and get this error that says run apt-get to correct. Full circle. 

Ratliff

HI and quote
2
With apt-get :
apt-get install debian-multimedia-keyring
And ignore the apt-get warnings about the missing GPG key.
From here
[http://www.debian-multimedia.org/](http://www.debian-multimedia.org/)
Edit sorry yabba
I have no idea why :)

---

### Post by yabbadabbadont on 2008-02-28
Why are you using non-Ubuntu repositories?  You get the error because you have not used "apt-key" to add those third party repo's GPG keys.  (assuming that they have them)

Edit: Too slow.

---

### Post by mandrill on 2008-02-29
> **yabbadabbadont said:**
> Why are you using non-Ubuntu repositories?  You get the error because you have not used "apt-key" to add those third party repo's GPG keys.  (assuming that they have them)

Edit: Too slow.

What are you trying to accomplish, exactly?

---

### Post by zvacet on 2008-02-29
gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
gpg --export --armor KEY | sudo apt-key add -


in your case you will type in terminal

gpg --keyserver hkp://subkeys.pgp.net --recv-keys 07DC563D1F41B907
gpg --export --armor 07DC563D1F41B907  | sudo apt-key add -

---

