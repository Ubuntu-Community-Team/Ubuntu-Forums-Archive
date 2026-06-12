---
title: "Error: gnome-keyring-pkcs11 not found"
date: 2012-05-05
forum: Installation &amp; Upgrades
---

### Post by Pooky5 on 2012-05-05
Hi guys,

I have little problem, I try run some windows app under wine but there is a problem.
I always get this error:

```
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: sdílený objektový soubor nelze otev&#345;ít: Adresá&#345; nebo soubor neexistuje
```Well, I found this file in another location - /usr/lib/x86_64-linux-gnu/pkcs11/gnome-keyring-pkcs11.so
I also try trick with symlink but nothing work. I should mention that I have Ubuntu 12.04 64bit edition.

Any idea how make this work? Meaby some 32bit library?

Thanks

---

### Post by vahid.alavi on 2012-05-05
> **Pooky5 said:**
> Hi guys,

I have little problem, I try run some windows app under wine but there is a problem.
I always get this error:

```
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: sdílený objektový soubor nelze otev&#345;ít: Adresá&#345; nebo soubor neexistuje
```Well, I found this file in another location - /usr/lib/x86_64-linux-gnu/pkcs11/gnome-keyring-pkcs11.so
I also try trick with symlink but nothing work. I should mention that I have Ubuntu 12.04 64bit edition.

Any idea how make this work? Meaby some 32bit library?

Thanks


I have the same problem and googled a lot. Finally I reached to symbolic link. But the classes are not same it seems.
Could anyone give any other suggestion?

Ubuntu 12.04 LTS
Wine1.4
program to run: SAP2000, dotnet20sp1

---

### Post by dfv78 on 2012-05-05
I also tried creating a link to the file following this suggestion: 
[http://ubuntuforums.org/showthread.php?p=11768305]("http://ubuntuforums.org/showthread.php?p=11768305")

I also get the Class error:

> p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: **wrong ELF class: ELFCLASS64**

Ubuntu 12.04 LTS
Wine1.5

---

### Post by Pooky5 on 2012-05-06
I found some topic in winehq forum, they said it's distro problem, so meaby we should report bug?

[http://forum.winehq.org/viewtopic.php?p=75702&sid=299b5d6b2979818ea46bef500ee7c057](http://forum.winehq.org/viewtopic.php?p=75702&sid=299b5d6b2979818ea46bef500ee7c057)

---

