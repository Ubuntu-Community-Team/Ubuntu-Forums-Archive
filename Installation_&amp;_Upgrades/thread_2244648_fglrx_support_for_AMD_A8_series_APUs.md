---
title: "fglrx support for AMD A8 series APUs?"
date: 2014-09-17
forum: Installation &amp; Upgrades
---

### Post by charles31 on 2014-09-17
I bought minecraft for my computer, which is running 12.04 ubuntu, and apparently I need to update my drivers.  

I was going to download the first option [http://support.amd.com/en-us/download/desktop?os=Linux+x86](http://support.amd.com/en-us/download/desktop?os=Linux+x86) here, but a friend warned to ask about "fglrx support for AMD A8 series APUs" beforehand, to see if these drivers will mess up my computer.

---

### Post by mastablasta on 2014-09-18
why do you need to update the drivers?

you could do a HWE update ([https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)) and then install new drivers from additional drivers app.

or you could just upgrade the whole thing to 14.04.1 and then install the proper drivers.

---

### Post by charles31 on 2014-09-18
[http://www.minecraftforum.net/forums/support/unmodified-minecraft-client/2217594-game-crashes-on-linux-just-bought-it?ukq624](http://www.minecraftforum.net/forums/support/unmodified-minecraft-client/2217594-game-crashes-on-linux-just-bought-it?ukq624)

The only response I got was to update my graphics card, which a friend also recommended.  This involves updating the drivers (I really don't understand this stuff myself), but another friend (who introduced me to linux but does not use it himself) told me to ask what I'm asking in this thread.

---

### Post by mastablasta on 2014-09-18
here are instructions to install fglrx (manually build from source or pre-packaged version): [https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)

a new Ubuntu version was out in April 2014 (another LTS supported for 5 years). it brings newer kernel (includes new AMD opensource drivers) and when you upgrade to it you can also install newer version of drivers from the additional drivers application or via command line...

you can of curse stay on current version and do some things manually. it's a bit more complicated but doable.

---

