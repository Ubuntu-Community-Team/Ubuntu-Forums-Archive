---
title: "Problem with GPG"
date: 2006-07-02
forum: Installation &amp; Upgrades
---

### Post by johlin on 2006-07-02
I read the guide in the wiki for installing InitNG, but I can't add the gpg-keys for the respository and without them the package refuses to compile.
I asked this in the IRC channel yesterday, but I didn't get a solution (even though a few people tried to help).
I posted in on pastebin, [link.]("http://pastebin.ca/76482?srch=gpg")

The .gnupg folder is owned by me, but I've tried giving it to root also.

---

### Post by rcarring on 2006-07-02
The gpgkey should reside in the folder in which the application is launched from, or in the path, or in home depeding on where the app launch command is spawned.

I had this problem with jre 1.4 and I had to make sure that the key was in the folder that I was trying to install from.

---

### Post by johlin on 2006-07-02
I solved it by changing the owner to root, even though I've heard that's bad, it works.

---

