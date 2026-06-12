---
title: "LTSP on Linux Mint 16 - MATE"
date: 2013-12-29
forum: MINT
---

### Post by norrie2 on 2013-12-29
Hi all,
I'm having a problem installing LTSP on LM16 (MATE).  Having followed [http://forums.linuxmint.com/viewtopic.php?f=190&t=83991](http://forums.linuxmint.com/viewtopic.php?f=190&t=83991) I did:
```
sudo ltsp-build-client --dist=saucy
```
This builds the thin client image and the test machine boots it and it seems to run fine.  However, I want to use fat clients so I did:
```
sudo ltsp-build-client --fat-client --dist=saucy
```
This also builds fine but the client boots and loads the standard Ubuntu unity desktop and it's also so slow that it's unusable.


Does anyone know what I need to do to get a correct fat client image please?


Many thanks,


NTB

---

