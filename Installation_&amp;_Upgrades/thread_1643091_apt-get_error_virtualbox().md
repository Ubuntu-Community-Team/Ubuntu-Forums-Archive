---
title: "apt-get error virtualbox(?)"
date: 2010-12-11
forum: Installation &amp; Upgrades
---

### Post by jperelli on 2010-12-11
Hello! :)

I have an annoying error everytime I run apt-get, this is the output (it's in spanish, yes)

atención, en archivo «/var/lib/dpkg/status» línea cercana 54830 paquete «virtualbox-3.0»:
 error en la cadeba de versión «3.0.14-58977_Ubuntu_karmic»: carácter inválido en el número de revisión
atención, en archivo «/var/lib/dpkg/status» línea cercana 54831 paquete «virtualbox-3.0»:
 error en la cadena Config-Version «3.0.14-58977_Ubuntu_karmic»: carácter inválido en el número de revisión
atención, en archivo «/var/lib/dpkg/available» línea cercana 670141 paquete «virtualbox-3.0»:
 error en la cadeba de versión «3.0.14-58977_Ubuntu_karmic»: carácter inválido en el número de revisión
atención, en archivo «/var/lib/dpkg/available» línea cercana 691199 paquete «virtualbox-2.0»:
 error en la cadeba de versión «2.0.12-53697_Ubuntu_karmic»: carácter inválido en el número de revisión



It says,
Warning, in file «/var/lib/dpkg/XXX» near line XXX package «virtualbox-X.0»:
error in version string «3.0.14-58977_Ubuntu_karmic»: Invalid character in revision number

I don't know what to do...

How can I get rid of this warnings?

Thanks in advance! ;)

---

### Post by sikander3786 on 2010-12-11
Try using an older status file.

Backup your existing status file.

```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.bad
```

```
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
```

```
sudo apt-get update
```

Hopefully, it shouldn't give that error. If it still does, edit your status file by,

```
gksudo gedit /var/lib/dpkg/status
```

And try to find the error or offensive character in lines 54830, 54831, 670141 and 691199. Correct that error, save and close and try again. If you can't figure that out, just post those lines here to let us take a look.

---

### Post by karthick87 on 2010-12-11
You can get the error messages in English if it is in other language,

```
sudo LANG=C apt-get update 
```

---

### Post by jperelli on 2011-05-12
> **karthick87 said:**
> You can get the error messages in English if it is in other language,

```
sudo LANG=C apt-get update 
```

Thanks! that's really useful to google something and find more results in english!!
Ill use it!

---

### Post by jperelli on 2011-05-12
Thanks!
I finally edited the file in that line, it seems that an underscore is an invalid char, I replaced it with a tilde "~", and now it doesn't give warns.

---

