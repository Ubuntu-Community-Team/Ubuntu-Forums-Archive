---
title: "Texlive dependency problems"
date: 2006-10-29
forum: Installation &amp; Upgrades
---

### Post by sav2005 on 2006-10-29
The installation of TeXLive via apt-get/synaptic fails with a lot of dependency problems. I removed the old tetex* but this did not fix the issue. I have tried "apt-get -f install" but now each time I install a program the list of teXlive dependencies appears.

Laurie

---

### Post by epud on 2008-01-21
Does anybody know the answer to this? I have the same problem.

---

### Post by Partyboi2 on 2008-01-21
Are you able to post the output to these commands from a terminal (Applications>Accessoires>terminal)
```
sudo apt-get update
``````
sudo apt-get upgrade
``````
sudo apt-get install -f
```

---

### Post by bernecky on 2008-01-21
I spent several days kicking my giant brain machine, in hopes of getting tex-live to
install. I finally got the configure to work. Here's what I found: 

My /etc/profile.local file defined:

export TEXMF=/usr/share/texmf
export TEXMFLOCAL=/usr/local/share/texmf

These were leftovers from an earlier SuSE incarnation.
When I commented out the two lines above, AND THEN
SIGNED OFF AND BACK ON(Didn't work otherwise...),
the configuration all worked nicely.

I'm not sure of the proper way to fix this, but I'm back on the air now.

rbe

---

