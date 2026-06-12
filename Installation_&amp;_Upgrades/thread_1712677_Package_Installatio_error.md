---
title: "Package Installatio error"
date: 2011-03-23
forum: Installation &amp; Upgrades
---

### Post by asif.kodur on 2011-03-23
well, as i waas installing sm packages my package installer or smthing seems to be broken. I was warned with a Msgbox, to install this thede items must be removed. i clicked 'install anyway''.

Anyway, now i cant use any of my package installers. Synaptic says' U hv one broken package' and refuses to work until it is fixed. But fixing also doesn't work.

Here are screenshots of terminal commands (*[FONT=Georgia]apt-get install -f[/FONT]*) and other msgs.

Thank u

---

### Post by zvacet on 2011-03-25
This is just a suggestion.Press alt+f2 and type 

```
gksudo nautilus
```

Go to the /var/cache/apt/archives and delete that package.Exit from there and type in terminal

```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade
```

---

