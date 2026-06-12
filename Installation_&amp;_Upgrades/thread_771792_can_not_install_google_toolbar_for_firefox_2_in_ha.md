---
title: "can not install google toolbar for firefox 2 in hardy"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by shelper on 2008-04-27
the system gives this error:
Error: installLocation has no properties
Source File: file:///usr/lib/firefox/components/nsExtensionManager.js
Line: 3938

any idea? i believe it should be a common problem
i am using ubuntu 8.04 AMD64

btw, another problem is i installed XFCE in ubuntu(gnome)
it gives the xfce loading interface but when i login, it is still gnome
any idea?

thanks alot!

---

### Post by gsoundsgood on 2008-05-01
it's a bug, it happened to me as well.

there's a solution on [launchpad]("https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/212644")

i hope they'll fix it...

---

### Post by jak.plopelor on 2008-05-12
what you do is this:

[COLOR="Red"]completely remove firefox on synaptic.[/COLOR]

then install it again.

then run on terminal:

[COLOR="Red"][COLOR="Lime"]rm -fr ~/.mozilla[/COLOR][/COLOR]

and then install the google toolbar.

hope this works

---

