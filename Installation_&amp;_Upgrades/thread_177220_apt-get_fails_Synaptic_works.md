---
title: "apt-get fails Synaptic works"
date: 2006-05-15
forum: Installation &amp; Upgrades
---

### Post by Bubba Ho-Tep on 2006-05-15
I've two Breezy machines - one has the Gnome desktop the other is the server install.

I'm trying to install RRDtool on the server machine and I get "has no installation candidate" error. Ok so i downloaded the tar.gz of RRDtool to install from source and now am getting deeper and deeper into dependency hell.

Getting pissed off with this I looked up RRDtool on Synaptic on the gnome box and it's there and it installs no worries.

What gives? why won't apt-get install on the server box and yet Synaptic has no problems on the gnome box?

---

### Post by nanotube on 2006-05-15
did you try updating apt-get (sudo apt-get update), before trying the "sudo apt-get install whatever" ?

---

### Post by Bubba Ho-Tep on 2006-05-16
yeah tried that...

---

### Post by wbmj on 2006-05-16
My guess is you need to edit your source list on the server. Try comparing the lists from both machines. You probably need to uncomment something on the server box. Just a guess

---

