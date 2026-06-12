---
title: "Problem installing Ati-driver in 11.04"
date: 2011-07-03
forum: Installation &amp; Upgrades
---

### Post by Raphael Barros on 2011-07-03
Hello people!  I'm trying to install ati-driver-installer-9-3-x86.x86_64.run in my laptop with radeon x1200 series. While installing, I got this:  > ./ati-driver-installer-9-3-x86.x86_64.run: linha 187: erro de sintaxe próximo do `token' não esperado `(' ./ati-driver-installer-9-3-x86.x86_64.run: linha 187: `    #        echo &quot;The program '$script' returned an error code ($res)&quot; >&2'    I'm using ubuntu 11.04 64 bits alternate.  I don't know any other way to install this driver, anyone could help me???

---

### Post by Mark Phelps on 2011-07-04
> **Raphael Barros said:**
> ... with radeon x1200 series

Put simply -- you can't!  

There is no AMD restricted driver that will work with that model Radeon and any Ubuntu version newer than 8.10.  AMD dropped Linux driver support for the X1200 series cards (and others) after that version.

You're stuck using the default open-source drivers -- which are installed automatically when you first setup the system.

---

### Post by Raphael Barros on 2011-07-04
Well, thanks for the answer. It's a pity, Though.

---

