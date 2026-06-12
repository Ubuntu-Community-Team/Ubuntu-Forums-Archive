---
title: "Install - Basic question"
date: 2006-06-25
forum: Installation &amp; Upgrades
---

### Post by aolong on 2006-06-25
All the docs I read indicate that booting the live cd will allow an install. I cannot find how. I get into X as user ubuntu but can find no install option or entry in the utilities anywhere. The install docs say booting will lead to partitioning options after keyboard etc... that does not happen, it goes right into x. The disc I had was live cd 5.10. Should I be downloading a different disc?

---

### Post by Agent86 on 2006-06-25
[QUOTE=aolong]The disc I had was live cd 5.10. Should I be downloading a different disc?[/QUOTE]

I don't think the Breezy Live CD is installable. The Dapper (6.06) Live CD is installable.

---

### Post by aolong on 2006-06-25
I'm downloading the 6.06 alternate now, will give that a whirl.

---

### Post by aysiu on 2006-06-25
[QUOTE=Agent86]I don't think the Breezy Live CD is installable. The Dapper (6.06) Live CD is installable.[/QUOTE]
I can confirm this. Breezy's live CD cannot install.
Dapper's Desktop and Alternate CDs can *both* install.

---

### Post by aolong on 2006-06-25
One more question I may as well ask here: I am not really interested in a preconfigured slew of packages, I want more control over what is installed. Will the alt cd allow me a minimum or menu install in which I can selct/deselect packages?

---

### Post by aysiu on 2006-06-25
You can do (from the Alternate Install CD) a server install and then ```
sudo aptitude update
sudo aptitude install x-window-system-core xterm gdm icewm menu firefox synaptic
``` and then just use Synaptic to install stuff.

Or if you're really comfortable with the terminal, do a server install and just type ```
aptitude
```

---

### Post by aolong on 2006-06-25
[QUOTE=aysiu]You can do (from the Alternate Install CD) a server install and then...[/QUOTE]

So by "server install" it means that just the httpd and other (server) essentials will be installed, none of the typical user packages (which I then add later)?

---

### Post by aysiu on 2006-06-25
Yes.

---

