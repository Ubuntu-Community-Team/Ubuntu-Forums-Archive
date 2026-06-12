---
title: "Signature error from apt-get update"
date: 2012-06-14
forum: Installation &amp; Upgrades
---

### Post by richpri on 2012-06-14
I am running UBUNTU 11.10 and my update manager has stopped working.
The apt-get update command returns the following error message:

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 52A794126E3AB2D3

How can I rectify this issue?

---

### Post by wojox on 2012-06-14
You could run these two commands in the terminal:
```
gpg --keyserver pgpkeys.mit.edu --recv-key  52A794126E3AB2D3     
```
```
gpg -a --export 52A794126E3AB2D3 | sudo apt-key add -
```

---

### Post by richpri on 2012-06-14
That seems to have done the trick!  Thanks a lot!

Note: I know that there has to be some way to mark this thread as solved but I can't figgure it out. Can anyone explain this or just do it for me?

---

### Post by black veils on 2012-06-14
just above this thread, **Thread Tools**

---

