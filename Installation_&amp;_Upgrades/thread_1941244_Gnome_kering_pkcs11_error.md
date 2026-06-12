---
title: "Gnome kering pkcs11 error"
date: 2012-03-15
forum: Installation &amp; Upgrades
---

### Post by otherethe on 2012-03-15
/usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory

any work arounds?
Ubuntu 12.04

---

### Post by bcarlowise on 2012-03-15
Sounds like whatever is trying to use the library is looking in a spot it does not reside. Try running the following command to find where on your system the file resides:

"sudo find / -name gnome-keyring-pkcs11.so"

Once the location of where the file resides is found, you can create a link to the file as follows:

cd /usr/lib/i386-linux-gnu/pkcs11

ln -s <location of where file resides> gnome-keyring-pkcs11.so

For example, on my system the above commands would be as follows:

cd /usr/lib/i386-linux-gnu/pkcs11

ln -s /usr/lib/pkcs11/gnome-keyring-pkcs11.so gnome-keyring-pkcs11.so

---

