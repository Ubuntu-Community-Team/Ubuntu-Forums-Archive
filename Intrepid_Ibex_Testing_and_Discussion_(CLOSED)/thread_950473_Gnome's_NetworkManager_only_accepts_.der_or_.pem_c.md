---
title: "Gnome's NetworkManager only accepts .der or .pem certificates; expected .crt support"
date: 2008-10-17
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by pedrogfrancisco on 2008-10-17
Hi!

To connect to my university wireless network I was used to select GTE_CyberTrust_Global_Root.crt from /usr/share/ca-certificates/mozilla .

However the new version of NetworkManager only allows one to select certificates which are *.der or *.pem .

I can workaround it by pasting the full filename in the window; NetworkManager accepts it apparently (as in "Doesn't pop up an error message"). However the question remains: is it a bug in NetworkManager? Should it allow one to select *.crt certificates? Or should it pop up an error message as it isn't supposed to accept *.crt certificates?

---

