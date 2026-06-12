---
title: "[SOLVED] OO plugin doesn't request password"
date: 2008-07-07
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Kevbert on 2008-07-07
Hi.  I'm using Kubuntu Intrepid Alpha1.  I've just installed some new dictionaries via DicOOo in OpenOffice Writer.  At present the only way I can normally install software is via the bash terminal where it asks for my login password.  Adept will only ask for a root password which I haven't setup yet.  With DicOOo it just downloads and installs software.  Is this a security vulnerability ?

---

### Post by JACooks on 2008-07-07
As I see it, OO is using a similar method that Firefox (and other Mozilla products) use for their Add-Ons.  The risk level for such items depends on the process that OO/Mozilla use to permit add-ons to be installed.  With Firefox, one can add virtually any site (using https, as of FF 3) to the safe list to allow installs.  I'm not sure this is a real security issue for Ubuntu, since by default, the user does not run OO as root.  I suppose if the user started the application using sudo it might be an issue, but that's an unlikely scenario.  I'm no security expert, but that's my two cents.

---

