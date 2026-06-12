---
title: "Onieric &quot;Partial Upgrade&quot; after a GIMP update leaves graphics problems?"
date: 2012-02-14
forum: Installation &amp; Upgrades
---

### Post by ZaydHumsy on 2012-02-14
So, I've fallen victim to this ( [http://ubuntuforums.org/showthread.php?t=1923311](http://ubuntuforums.org/showthread.php?t=1923311) ) problem in 11.10, and so I followed the recommended steps and, not only does GIMP still not install, but I can't run any updates (due to it requesting ANOTHER partial upgrade that can't authenticate basic packages like gnome_shell), and I've been having graphical bugs in the UI elements like this: [http://i.imgur.com/lEGAC.png]("http://i.imgur.com/lEGAC.png")

Anyone know anything that can help?

---

### Post by ZaydHumsy on 2012-02-14
A last resort is a reinstall, but I would hope to find another solution.

---

### Post by ajgreeny on 2012-02-14
I would totally remove the ppa by disabling it and removing it using synaptic (much better than the software-centre) or the ppa-purge package from [http://www.google.co.uk/url?sa=t&rct=j&q=ppa%20purge&source=web&cd=1&ved=0CDAQFjAA&url=https%3A%2F%2Flaunchpad.net%2Fppa-purge&ei=GOo6T5OzEZO5hAemm7WJCg&usg=AFQjCNFix_GEA9k5m2_nOPEpXdnyHooFNA&cad=rja](http://www.google.co.uk/url?sa=t&rct=j&q=ppa%20purge&source=web&cd=1&ved=0CDAQFjAA&url=https%3A%2F%2Flaunchpad.net%2Fppa-purge&ei=GOo6T5OzEZO5hAemm7WJCg&usg=AFQjCNFix_GEA9k5m2_nOPEpXdnyHooFNA&cad=rja), then totally remove gimp, plus all the other packages that it depends upon, and finally reinstall gimp again but not with the unstable 2.7.x version you have been using but the stable 2.6.11, or whatever it is in oneiric.

The packages that are updated or added in Lucid when the gimp 2.7 ppa is used are:-

libopenraw1
libbabl-0.0-0
libgegl-0.0-0
gimp
libgimp2.0
libamd2.2.0
libumfpack5.4.0
gimp-data

but they may be different in oneiric, but this list may help you remove anything that is causing a problem.

---

