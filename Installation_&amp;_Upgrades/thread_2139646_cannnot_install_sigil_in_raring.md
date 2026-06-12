---
title: "cannnot install sigil in raring"
date: 2013-04-27
forum: Installation &amp; Upgrades
---

### Post by frank.bommeli on 2013-04-27
I just made a clean install of Ubuntu 13.04.

I tried to install Sigil, but couldn't do it :(

I don't see what I can do wrong. I followed the instruction as specified [http://handytutorial.com/install-sigil-epub-editor-in-ubuntu-12-10-12-04-from-ppa/](http://handytutorial.com/install-sigil-epub-editor-in-ubuntu-12-10-12-04-from-ppa/).

i.e.,
```

sudo add-apt-repository ppa:rgibert/ebook
sudo apt-get update
sudo apt-get install sigil

```

I got the following error:
```

E: Unable to locate package sigil

```

If I check the package at [http://ppa.launchpad.net/rgibert/ebook/ubuntu/](http://ppa.launchpad.net/rgibert/ebook/ubuntu/)
I see that there is a package defined for raring.

I made some tries with the GUI, but was not more successful.

Any help would be appreciated

Frank

---

### Post by dino99 on 2013-04-27
add-apt-repository have set that ppa to "raring", BUT looking at it, the newest it has is "oneiric" (quite old, meaning not maintained)

either change the distro inside synaptic for that ppa, or use an other one, like : [https://launchpad.net/~sunab/+archive/sigil-git](https://launchpad.net/~sunab/+archive/sigil-git)

---

### Post by frank.bommeli on 2013-04-27
Thanks a lot dino99 this solved my problem :)

---

