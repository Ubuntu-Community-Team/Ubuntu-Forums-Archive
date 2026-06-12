---
title: "Anyone else having trouble installing Adobe Reader with Karmic 64?"
date: 2009-07-07
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Slug71 on 2009-07-07
Just wondering if this is Karmic specific. I had Adobe Reader working fine with Jaunty 64 but i just tried to install it on Karmic with the .deb package and get these errors:

I get the "wrong architecture" message with gdebi(i have the 32bit libs installed) and if i run in terminal:
```

sudo dpkg -i --force-all AdbeRdr9.1.1-1_i386linux_enu.deb
```

i get

> dpkg: error processing AdbeRdr9.1.1-1_i386linux_enu.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 AdbeRdr9.1.1-1_i386linux_enu.deb

Am i forgetting something?

---

### Post by Darkshade on 2009-07-07
You can get the 64bit deb from medibuntu ( [http://packages.medibuntu.org/karmic/acroread.html](http://packages.medibuntu.org/karmic/acroread.html) ) or just add their repo and install the package "acroread"

---

### Post by lithorus on 2009-07-07
You're trying to install an 32-bit package on a 64-bit system. Ofcourse you're getting problems...
Try with this repo :
> deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic free non-free
Edit:
Bah, too late :)

---

### Post by cariboo on 2009-07-07
I installed Acrobat from the Medibuntu repositories, I had zero problems.

---

### Post by zenarcher on 2009-07-07
> **cariboo907 said:**
> I installed Acrobat from the Medibuntu repositories, I had zero problems.

Same here.  The Medibuntu repository install worked just fine.

Cheers,
zenarcher

---

### Post by Slug71 on 2009-07-07
> **lithorus said:**
> You're trying to install an 32-bit package on a 64-bit system. Ofcourse you're getting problems...
Try with this repo :

Edit:
Bah, too late :)

Like i said, never had issues doing this with Jaunty. 

that repo worked though, thanks. :p

---

