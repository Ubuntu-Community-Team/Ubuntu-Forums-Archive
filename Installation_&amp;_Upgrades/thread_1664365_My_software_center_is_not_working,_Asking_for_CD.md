---
title: "My software center is not working, Asking for CD"
date: 2011-01-10
forum: Installation &amp; Upgrades
---

### Post by seckin on 2011-01-10
Hi Everyone,

How do I get rid of this ? My software center is not working and it keeps asking for this cd rom. 

seckin@seckin-System:~$ sudo apt-get update
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007) maverick Release.gpg
Media change: please insert the disc labeled                                   
 'Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007)'
in the drive '/cdrom/' and press enter

Thanks,
Seckin

---

### Post by matt_symes on 2011-01-10
Hi

System->Administration->Software sources.

Uncheck the CDRom option on the Ubuntu software tab.

Kind regards

---

### Post by seckin on 2011-01-10
thanks.

---

### Post by Darris on 2011-03-08
That didn't work for me. 
I don't have that option under system>administration
Is there something wrong with my ubuntu?

---

### Post by matt_symes on 2011-03-08
Hi

Post the output of (from a terminal)

```
cat /etc/apt/sources.list
```

Kind regards

---

### Post by Dutch70 on 2011-03-08
> **Darris said:**
> That didn't work for me. 
I don't have that option under system>administration
Is there something wrong with my ubuntu?

No, software sources is not included in the menu options for 10.10, you have to add it. 
[[COLOR="Blue"]http://www.webupd8.org/2010/09/software-sources-disabled-from-ubuntu.html[/COLOR]]("http://www.webupd8.org/2010/09/software-sources-disabled-from-ubuntu.html")

---

### Post by neoroses on 2011-03-08
not at my linux box atm but you can change it by opening synaptic package manager and going to sources. 

Safe. :)

---

### Post by lupo1939 on 2011-03-08
FYI:  Under 10.10 System->Administration->Software sources.
Software Sources is inside Update Manager.

---

### Post by Frogs Hair on 2011-03-08
Update Manager > Settings > Other Software

---

