---
title: "Karmic 9.10 Proxy Authentication"
date: 2009-10-01
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ogryn on 2009-10-01
Hello,

I've just installed KarmicA6 after my previous 9.04 HDD failed. Being at work and behind a Squid proxy which uses Windows Domain authentication, I'm having some issues connecting.

I can enter the proxy and auth details in the Gnome Proxy settings (and have to put in my password TWICE to "Apply System-Wide"), and also put the same settings into Synaptic.

However, if I want to use Ubuntu Software Store or Update Manager it fails with a 407 Proxy Authentication error. Synaptic works fine however.

(I can't connect to GTalk either because of Empathy's lack of Proxy configuration! I used to have to select "No Proxy" in Pidgin to get it to work...)

Any ideas why this isn't working well? Does it make any difference authenticating as [DOMAIN]\[username] as opposed to just [username]? I may have to resort to CNTLM although that seems like a bit of a hack.

---

