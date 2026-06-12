---
title: "How to add a .deb file to apt-get?"
date: 2006-10-31
forum: Installation &amp; Upgrades
---

### Post by 67comet on 2006-10-31
I've got myself a subscription to Transgaming, however the .deb they let give you isn't working fully.

I tossed it into /var/cache/apt/archhives and updated synaptic. It shows up as installed (I did dpkg -i cedega-small.deb). I uninstalled it via synaptic, and attempted to re-install it but it goes so far then tells me:

 sudo apt-get install cedega-small 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package cedega-small is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package cedega-small has no installation candidate

I've also been wondering if I just installed wine it would take care of what cedega offers?

Thanks,
Justin

---

### Post by Kateikyoushi on 2006-10-31
Isn't it enough if you install the package with dpkg ?
I think that should do it.

Cedega install instructions. [LINK]("http://downloads.transgaming.com/files/cedega_quick_start_5.2.html#0.0.0.DEB|outline")

---

### Post by michux on 2006-10-31
> **67comet said:**
> I've got myself a subscription to Transgaming, however the .deb they let give you isn't working fully.

Just double-click on the DEB file and gdebi will take care of the rest of the installation for you!

If you prefer the command line, type: ```
dpkg -i package_name.deb
```

---

