---
title: "Strange apt errors after hoary upgrade..."
date: 2005-04-24
forum: Installation &amp; Upgrades
---

### Post by BigRod on 2005-04-24
After I upgraded to hoary, now I get the following errors every time I run an update, upgrade, or check (not sure about install, haven't tried that yet).  This is what I got after an apt-get update (notice that it suggests running an update to correct the problem).

```
W: GPG error: ftp://ftp.nerim.net stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: GPG error: ftp://ftp.nerim.net unstable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: GPG error: ftp://ftp.nerim.net testing Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: You may want to run apt-get update to correct these problems

``` 

Any ideas?

---

### Post by BAshworth on 2005-04-24
What are the nerim repositories in your sources.list file?  For Hoary, they should be.

```

deb ftp://ftp.nerim.net/debian-marillat stable main
deb ftp://ftp.nerim.net/debian-marillat unstable main
deb ftp://ftp.nerim.net/debian-marillat testing main

```

---

### Post by Leif on 2005-04-24
follow this :

[http://www.ubuntulinux.org/wiki/AptAuthenticationInstructionsForHoary](http://www.ubuntulinux.org/wiki/AptAuthenticationInstructionsForHoary)

---

### Post by BigRod on 2005-04-24
[QUOTE=BAshworth]What are the nerim repositories in your sources.list file?  For Hoary, they should be.

```

deb ftp://ftp.nerim.net/debian-marillat stable main
deb ftp://ftp.nerim.net/debian-marillat unstable main
deb ftp://ftp.nerim.net/debian-marillat testing main

```[/QUOTE]

Those are the ones that I have.

---

### Post by BigRod on 2005-04-24
[QUOTE=Leif]follow this :

[http://www.ubuntulinux.org/wiki/AptAuthenticationInstructionsForHoary](http://www.ubuntulinux.org/wiki/AptAuthenticationInstructionsForHoary)[/QUOTE]

Cool, that fixed it.

Thanks!

---

