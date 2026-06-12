---
title: "Ubuntu studio 64 not in synaptic?"
date: 2008-11-23
forum: Installation &amp; Upgrades
---

### Post by thelowreysfour on 2008-11-23
i recently got ubuntu 8.10 64 using wubi.  I would like to upgrade to ubuntustudio.  I am new to this and am a little confused with synaptic. It took some looking for studio in the manager. 

there is no 64 bit ubuntustudio listed in synaptic. there are several packages though for the 32 bit (or i assume)

I have seen some posts that say i can add 64 to the code below and comand line it. but where do i add the 64?  being new i would rather use synaptic.  PLEASE HELP

Sudo aptitude install ubuntustudio-desktop

---

### Post by cariboo on 2008-11-23
Go to Synaptic-->Edit->Mark Packages by Task, and scroll down you will see **Ubuntu Studio desktop (must install)**. Just put a check mark beside it and click OK. A window will pop up that says Mark Additional required changes?, just click mark then click apply, and you should be on your way to install the Ubuntu Studio desktop.

Jim

---

### Post by thelowreysfour on 2008-11-23
does it matter if it does not say 64? will this be the entire package or will i have to install other packages?

---

### Post by specvthis on 2008-11-23
If you installed a 64 bit version of ubuntu (most likely) Synaptic knows this and will only install 64 bit applications. It does not need to specifically say 64.

---

### Post by thelowreysfour on 2008-11-23
thank you that is exactly what i needed to know.

---

