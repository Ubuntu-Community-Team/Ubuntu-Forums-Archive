---
title: "apt-get update fails"
date: 2006-07-10
forum: Installation &amp; Upgrades
---

### Post by JimBodkins on 2006-07-10
... with this

W: GPG error: [http://mirrors.kernel.org](http://mirrors.kernel.org) sarge Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 010908312D230C5F
W: You may want to run apt-get update to correct these problems



I have no idea what to do about this.


Ideas?

Jim

---

### Post by diepruis on 2006-07-10
This has to do with gpg, which is used to authenticate packages.
Try

```
gpg --import 010908312D230C5F

gpg --export --armor 010908312D230C5F | sudo apt-key add -
```

For more information see man gpg, [wikipedia]("http://en.wikipedia.org/wiki/Gpg").

---

### Post by JimBodkins on 2006-07-10
Thanks for the response.

Your idea produced this ...


root@devel:/usr/chms# gpg --import 010908312D230C5F gpg: can't open `010908312D230C5F': No such file or directory
gpg: Total number processed: 0

root@devel:/usr/chms# gpg --export --armor 010908312D230C5F | sudo apt-key add -gpg: WARNING: nothing exported
gpg: no valid OpenPGP data found.

---

### Post by diepruis on 2006-07-10
Meh! Sorry, I had the wrong syntax there. :oops:

Try
```

gpg --keyserver subkeys.pgp.net --recv-keys 2D230C5F 
gpg --export --armor 2D230C5F | sudo apt-key add -

```

This time I tested it properly, twice. :roll:

---

### Post by JimBodkins on 2006-07-10
Thanks :)

---

### Post by diepruis on 2006-07-10
Glad to be of help ;)

---

