---
title: "[SOLVED] checking md5sum"
date: 2008-11-26
forum: Installation &amp; Upgrades
---

### Post by razy60 on 2008-11-26
I have just downloaded a copy of 8.10 and want to check the md5sum.
I followed the instructions on checking the md5sum in Linux using terminal but all i get when i type, CD download_directory. is no such directory,
The file i downloaded appears as a ISO file on my desktop, I've extracted the file and tried it that way still no joy. Obviously I'm doing it wrong but not sure what,
Any help appreciated.

Raz

---

### Post by iKonaK on 2008-11-26
```
cd /to/iso/directory
openssl dgst -md5 *.iso
```hope it helps :)

---

### Post by razy60 on 2008-11-26
iKonaK wrote> cd /to/iso/directory
openssl dgst -md5 *.iso
Nope still no such file or directory.
Cheers though

Raz

---

### Post by aheckler on 2008-11-26
If the ISO is on your desktop, then:

```
cd ~/Desktop
md5sum nameofiso.iso
```

---

### Post by razy60 on 2008-11-26
aheckler wrote > cd ~/Desktop
md5sum nameofiso.iso

cheers that did it

Raz

thanks on the way:guitar:

---

