---
title: "Adept crashes on opening"
date: 2008-07-04
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by caryb on 2008-07-04
As the title says adept crashes soon after opening on my machine, does this happen to others running KDE4?


Cary

---

### Post by STEVE555 on 2008-07-04
Hi,
  Yes I can confirm that adept crashes soon after loading it.
The best way to update at the moment is to open Konsole and then either use

sudo apt-get update or

sudo apt-get dist-upgrade.

Regards,
       STEVE555

---

### Post by TFrog on 2008-07-08
I can also confirm that both Adept updater and Adept don't currently work in Kubuntu 8.10 Intrepid Ibex yet.  I can't even get KDEsu to authenticate and I'm running 8.10 in a virtual machine via Virtualbox 1.6.2.  Hopefully they get this fixed before Alpha 2.  Bug has been submitted on KDEsu issue.  Till then, best use Konsole and sudo apt-get update and sudo apt-get upgrade.

---

