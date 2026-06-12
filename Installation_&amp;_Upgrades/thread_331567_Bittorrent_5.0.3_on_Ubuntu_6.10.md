---
title: "Bittorrent 5.0.3 on Ubuntu 6.10"
date: 2007-01-04
forum: Installation &amp; Upgrades
---

### Post by Ubempi on 2007-01-04
How can I install the last version of Bittorrent on Ubuntu? (that which appears in this page [http://www.bittorrent.com/download.html](http://www.bittorrent.com/download.html) )

Here is what happened:

I just downloaded bittorrent: 
    Linux deb, Latest Release (5.0.3) recommended for all users 
from: 
    [http://www.bittorrent.com/download.html](http://www.bittorrent.com/download.html)

tried to install
and the installation finishes with:
    Error: Conflicts with the installed package 'bittorrent'

So I went to Synaptic and it says:
    Installed version: 3.4.2-6ubuntu3 / Last version: 3.4.2-6ubuntu3

I tried to uninstall it and Synaptic says:
    To be eliminated:
        gnome-btdownload
        ubuntu-desktop

That last may be wrong, I cannot uninstall the package 'ubuntu-desktop' so I cancelled it.

Now I don't know how to install Bittorrent 5.0.3

---

### Post by bruenig on 2007-01-04
You can uninstall ubuntu-desktop, it is just a meta package that calls on all the other packages during installation. Removing it poses absolutely no harm.

---

