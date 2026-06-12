---
title: "Nouveau Drivers and Gallium 3D"
date: 2010-02-05
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by donniezazen on 2010-02-05
Hi All,

Are you guys testing Nouveau drivers? How is it going?

Have you tried Gallium 3D? Is it for getting 3D Cube? What other things need 3D effect? Do i need it?

So if i install Nouveau i don't have to install Nvidia restricted drivers?

> sudo add-apt-repository ppa: xorg-edgers/nouveau

Thanks,
SK.

---

### Post by donniezazen on 2010-02-05
Other thing is this guide still good.

[http://ubuntuforums.org/showthread.php?p=6592005](http://ubuntuforums.org/showthread.php?p=6592005)

Do i have to do installation of both 2D and 3D?

Thanks.

---

### Post by nanog on 2010-02-07
there is no gallium 3d in ubuntu unless you install it via git. even xorg-edgers (fresh x crack) does not include gallium.

if you know what you are doing try this:
[http://nouveau.freedesktop.org/wiki/GalliumHowto](http://nouveau.freedesktop.org/wiki/GalliumHowto)

either way you are likely to hose your install. ;)

---

### Post by RAOF on 2010-02-07
To build current git you'll need the newer dri2 protocol headers from the main xorg-edgers repository.

If you build according to the gallium howto linked above there's very little chance of breaking anything, as you're not actually going to install the library systemwide.

For me, with a laptop with an nv4b card (GeForce 7600GO) in it, nouveau's gallium *currently* provides acceptable compiz & gnome-shell performance.  This will likely change - gallium has been broken and fixed and broken again multiple times.

---

### Post by donniezazen on 2010-02-07
Thanks for the info. For some reason i am not able to run Nouveau. I am not able to even get to GDM with nouveau drivers.

Xorg is a big show stopper. Every update of xorg breaks my system. I have to hard shutdown my system. Restart, enter key hangs, sometimes  i don't get GDM. We have 3 Alpha release and rest beta so that more people can test but if you are just not able to run it largely because of xorg, i doubt it that many people will like to test it.

Sorry, i am not blaming anybody, i am just a little upset and frustrated with xorg.

Thanks.

---

### Post by SevenMachines on 2010-02-07
are you using the new nouveau test driver from xorg-edgers nouveau ppa? 
[https://launchpad.net/~xorg-edgers/+archive/nouveau](https://launchpad.net/~xorg-edgers/+archive/nouveau)

---

### Post by donniezazen on 2010-02-07
> **SevenMachines said:**
> are you using the new nouveau test driver from xorg-edgers nouveau ppa? 
[https://launchpad.net/~xorg-edgers/+archive/nouveau](https://launchpad.net/~xorg-edgers/+archive/nouveau)

Yes i used this ppa. My Enter key is still freezing the system.

---

