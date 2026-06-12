---
title: "Ubuntu 6.10 hangs on boot"
date: 2007-02-23
forum: Installation &amp; Upgrades
---

### Post by Chris107 on 2007-02-23
I'm trying to boot the 6.10 installation CD but it will always hang right after the splash screen and there would be a colored line going through the screen.

Here's a crappy picture but you get the idea
[IMG]http://img412.imageshack.us/img412/5734/set3601vq3.jpg[/IMG]

I can install 6.06 just fine and upgrade from there but then my ATI drivers stop working and I get stuck with MESA.  I would prefer to have a fresh install of Edgy.

Any help would be appreciated.

---

### Post by Chris107 on 2007-02-23
b

---

### Post by logos34 on 2007-02-23
could be a corrupt download and/or bad burn.  Did you verify the checksum of the iso and burn it at 4x speed or less?

If this is the livecd, you could also try the text-mode alternate install cd.

---

### Post by Chris107 on 2007-02-23
I burned it twice and the same disc works fine on my laptop

---

### Post by Kateikyoushi on 2007-02-23
Did you try the safe video mode ?

---

### Post by Scotty562 on 2007-02-24
Same problem here man. Did you find a solution?

---

### Post by barrykooda on 2007-02-24
Is there a way to verify ISO checksum before burinig the disk?

---

### Post by ebichuhamster on 2007-02-24
My Ubuntu also hands after the image you portrayed.  Version 6.06 seems to be more stable so I'm going to try that.  I haven't tried burning the image at slower speed, nor do I even now how to check the sum thingy.  I know I'm such a noob at all this, so any guidelines to Edgy would help so much

---

### Post by Chris107 on 2007-02-24
Ok I got it to install using the alternate install disk in text mode.  Something with the default display driver didn't want to play nice with my Radeon X700 Pro so after installing I boot in recovery mode and install the fglrx drivers like I normally would.

---

