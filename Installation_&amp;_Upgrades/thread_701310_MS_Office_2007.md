---
title: "MS Office 2007"
date: 2008-02-19
forum: Installation &amp; Upgrades
---

### Post by Shippou on 2008-02-19
Uhmmm... Maybe most of you may disregard what will I ask, but then here it goes:

How do you install Microsoft Office 2007 in Ubuntu?


--> I admit that I don't like OpenOffice. Most of my dormmates too.

---

### Post by bernied on 2008-02-19
You do understand that Microsoft doesn't write software for linux? So it's not going to be easy.

I've done this using a virtual machine running Windows XP. Both vmware and VirtualBox have worked for me and both have free (as in beer, not speech) versions. But you do have to install Windows as well, so to do this legally, you need to have a valid Windows licence.

You could also try [wine](http://www.winehq.org/), which you would not need a windows licnece for, but I wouldn't expect this to be easy either.

Good luck!

[EDIT]Hmmmm, [this](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9313) doesn't look very encouraging:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=9313](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9313)

---

### Post by ThaRabbit on 2008-02-19
I can't tell you how to install Office 2007 under Ubuntu, given recent developments you're probably best off installing virtualbox or VMWare, installing windows XP inside a virtual machine and installing office 2007 there.

Alternatively, openoffice can open / save the docx format using a filter package:
[http://www.getdeb.net/search.php?search_distro_id=5&keywords=openxml](http://www.getdeb.net/search.php?search_distro_id=5&keywords=openxml)

If memory serves me right, this package is installable via Automatix:
[http://www.getautomatix.com/](http://www.getautomatix.com/)

And perhaps even via the default ubuntu repositories :)

note that this filter only works for the docx format, this does not yet work for the excel / powerpoint files.

OpenOffice 3.0 will support the ooxml format used by the office 2007 suite.

---

### Post by Shippou on 2008-02-19
> **bernied said:**
> You do understand that Microsoft doesn't write software for linux? So it's not going to be easy.

I've done this using a virtual machine running Windows XP. Both vmware and VirtualBox have worked for me and both have free (as in beer, not speech) versions. But you do have to install Windows as well, so to do this legally, you need to have a valid Windows licence.

You could also try [wine](http://www.winehq.org/), which you would not need a windows licnece for, but I wouldn't expect this to be easy either.

Good luck!

[EDIT]Hmmmm, [this](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9313) doesn't look very encouraging:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=9313](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9313)

I've tried installing through wine, but then it always says "insert cd" or something like that.

Thanks for the info. Anyway, are there other software that is equivalent to VMWare? I have difficulty installing it.

---

### Post by zeller on 2008-02-19
VirtualBox is decent. I haven't had any trouble with it.

---

### Post by GearedForWar on 2008-02-19
> **Shippou said:**
> I've tried installing through wine, but then it always says "insert cd" or something like that.

Thanks for the info. Anyway, are there other software that is equivalent to VMWare? I have difficulty installing it.


Well the cd is so they know its not a pirated version.  But if you are to ever get past that and install it, even though Wine may fail, go to the WINE settings and set the OS Sys32 files to Vista.

---

