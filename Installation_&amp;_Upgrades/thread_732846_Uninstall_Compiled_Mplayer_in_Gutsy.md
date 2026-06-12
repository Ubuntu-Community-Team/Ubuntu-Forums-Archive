---
title: "Uninstall Compiled Mplayer in Gutsy"
date: 2008-03-23
forum: Installation &amp; Upgrades
---

### Post by ElSimo on 2008-03-23
Does anyone know how to completely remove a compiled version of Mplayer from a Gutsy install? I don't really know the path that it was installed to and I'm pretty sure I deleted the compiled source after the install. Anyone run by this before? 

Cheers!

---

### Post by Oldsoldier2003 on 2008-03-24
> **ElSimo said:**
> Does anyone know how to completely remove a compiled version of Mplayer from a Gutsy install? I don't really know the path that it was installed to and I'm pretty sure I deleted the compiled source after the install. Anyone run by this before? 

Cheers!

if you used make checkinstall you can use dpkg -r or apt-get to remove it. If you used make install you have to run make install remove on the source ocde or manually rmeove the app.

to find the path do 
```
which <application_name>
```

---

### Post by ElSimo on 2008-03-26
Thanks for help. I got the source code again and uninstalled with the make command. Worked like a charm.

---

