---
title: "synaptic doesn't show any broken packages"
date: 2008-08-11
forum: Installation &amp; Upgrades
---

### Post by TuxIsCute on 2008-08-11
I just upgraded from Eft to Hardy and now I'm being told I have "held broken packages."  This normally wouldn't be frustrating as I know Synaptic is usually a friend and will nicely show which packages are broken and even fix them if it can--normally this is the case.  However my good friend has let me down for the first time.  I thought, hmm... broken packages let's get that fixed.  I launched synaptic and looked for the broken bugger.  At first I used the broken filter with no results.  Then I looked manually and still found nothing.  I aligned the packages based on if they were installed, broken, or marked, so on and so forth and still no broken packages could be located.  I tried edit -> fix broken command and still nothing--although synaptic announced dependency problems were fixed successfully.  I still cannot install anything because synaptic has locked the system thinking something is wrong.  If anyone out there can help, I've run out of options aside from re-installing Eft or Dapper and hoping the system doesn't do that again.

I await a reply.

Tux Is Cute (He really is)

---

### Post by Partyboi2 on 2008-08-13
What happens if you try to fix broken package from the terminal?
```
sudo apt-get -f install
```

---

