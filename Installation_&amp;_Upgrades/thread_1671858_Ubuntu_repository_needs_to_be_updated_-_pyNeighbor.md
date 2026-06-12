---
title: "Ubuntu repository needs to be updated - pyNeighborhood"
date: 2011-01-20
forum: Installation &amp; Upgrades
---

### Post by neutron68 on 2011-01-20
I just contacted the developers of pyNeighborhood via their webpage:
[http://launchpad.net/pyneighborhood](http://launchpad.net/pyneighborhood)

They suggested using the newer version of pyNeighborhood.  Unfortunately, the older version is in the Ubuntu repositories. 

**How can we get the newer version into the Ubuntu repository??**

> 
version 0.5.0x is outdated. We've fixed several Bugs and Errors in this version. Maybe you will try our PPA ([https://launchpad.net/~pyneighborhood/+archive/stable](https://launchpad.net/~pyneighborhood/+archive/stable)) to install the latest version 0.5.3. This version contains lots of improvements and bugfixes. Besides, its easier to find errors (we've added a debug-area). Unfortunately, the ubuntu archives only contain the outdated version pyneighborhood 0.5.0.

Please try this version and report any bugs you may encounter. If you have problems with installing pyneighborhood, I sure can provide help.

Greetz,

Linus

---

### Post by neutron68 on 2011-01-21
I got the new version (0.5.3) into my system by trying the advice on the pyNeighborhood page:
[http://launchpad.net/~pyneighborhood/+archive/stable](http://launchpad.net/~pyneighborhood/+archive/stable)
I clicked on the link that says "Technical details about this PPA".

I added these lines to my "/etc/apt/sources.list" file:
deb [http://ppa.launchpad.net/pyneighborhood/stable/ubuntu](http://ppa.launchpad.net/pyneighborhood/stable/ubuntu) maverick main
deb-src [http://ppa.launchpad.net/pyneighborhood/stable/ubuntu](http://ppa.launchpad.net/pyneighborhood/stable/ubuntu) maverick main

I launched the Synaptic Package manager and clicked UPDATE.

I searched for pyNeighborhood, right-clicked on it and selected the update choice.

I clicked APPLY.

I've now got 0.5.3 on my Mythbuntu 10.10 machine. I started it and right away it found all my shared computers without ANY configuration from me.

I can SEE the files in the SAMBA and Windows shares! WOO HOO!

**I still think it is a good idea to update the Ubuntu repository with version 0.5.3 - given that it works fine and version 0.5.0 does NOT work!**

Who should be contacted about updating the repository?

Thanks
Eric

---

