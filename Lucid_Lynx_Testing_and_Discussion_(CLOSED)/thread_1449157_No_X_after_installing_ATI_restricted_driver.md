---
title: "No X after installing ATI restricted driver"
date: 2010-04-07
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by RodrigoRodrigues on 2010-04-07
I am using Kubuntu 10.04 (Beta).

The notebook is a HP Pavilion Tx2510us and the video card is a Radeon HD 3200.

The native driver works fine but I need the restricted for vmware+gamedevelopment.

after installing and rebooting X is broken... if I try startx I get

... (lots of "no matching device for instance")
Failed to load module "fglrxdrm" (module does not exist, 0)
Failed to load DRM library
PreInit failed
Screen(s) found, but none have usable configuration.
Fatal server error: No screens found
...

if I delete /etc/X11/xorg.config X works without composition and I can uninstall the driver.

Any ideas?
Thanks

---

### Post by Mark Phelps on 2010-04-08
The new beta is known to have display issues, which is why you should be posting your 10.04-related questions to the proper beta testing forum: Development & Programming, Lucid Lynx Testing.

---

### Post by TrueJournals on 2010-04-08
What version of the driver do you have installed?  Did you run sudo aticonfig --initial after installing the driver?  Have you used fglrx without problems in a previous version of Ubuntu?

---

### Post by emarkay on 2010-04-08
> **Mark Phelps said:**
> The new beta is known to have display issues, which is why you should be posting your 10.04-related questions to the proper beta testing forum: Development & Programming, Lucid Lynx Testing.


Abracadabra! It magically appeared here, now...

OP - yea me too and a bunch of others - "stay tuned"...  :)

---

