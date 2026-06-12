---
title: "Error message in the synaptic manager about public key"
date: 2005-03-11
forum: Installation &amp; Upgrades
---

### Post by taniwha on 2005-03-11
When I reload my repositories I got this error message:

[B]W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907[/B]

I can install stuff, but I do not know why I get this message and how to sort it out.
Thanks

---

### Post by alastair on 2005-03-11
What it says really. The public key for these packages can't be found - so the packages cannot be verified as being what they claim to be i.e. there is a security risk.

---

### Post by edebont on 2005-03-11
[QUOTE=alastair]What it says really. The public key for these packages can't be found - so the packages cannot be verified as being what they claim to be i.e. there is a security risk.[/QUOTE]

To add the public key to your system (so the error messages won't appear again)

Open up a console and type the following commands:

gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 1F41B907
gpg --export 1f41B907 > /etc/apt/marillat.key
apt-key add /etc/apt/marillat.key

If you run apt-get update you shouldn't see any error messages.

---

