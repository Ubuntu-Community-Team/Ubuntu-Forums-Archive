---
title: "Upgrading Graphics Drivers in Ubuntu"
date: 2011-03-29
forum: Installation &amp; Upgrades
---

### Post by Dorakara on 2011-03-29
Hello everyone!
I have recently purchased a new Zotac 430 GT graphics card and I am wondering how to install new graphics drivers? I have downloaded the file from Nvidia's site but every time I try to use it it tells me that I must close the Nvidia X server before I install those. How does one go about doing this? This is probably a very easy question however I am still learning Ubuntu, as this is the first time I have had to install new graphics drivers.
My Ubuntu version is 10.10

Thanks a plenty!
Dorkara

P.S. If possible can you explain it as simple as possible as I have rarely had to open the terminal since I began using Ubuntu :) much obliged

---

### Post by mikewhatever on 2011-03-29
Here is a very comprehensive howto:
[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

However, if you are new to Ubuntu, why not start with System->Administration->Additional Drivers?

---

### Post by Dorakara on 2011-03-30
Thank you very much I will try this guide :)
and that is what I have been using but I figured i might need to upgrade them with my new graphics card(old windows habit, not sure if it applies here)

---

### Post by mikewhatever on 2011-03-30
You should probably know, that after manually installing the driver, you'll have to redo it after every kernel update. It's not the most convenient set up, but hope it's worth the trouble.

---

### Post by Dorakara on 2011-03-30
well do the updates to the graphic drivers help at all in gaming? or is it just something unnecessary for use?

---

### Post by mikewhatever on 2011-03-30
Depends. New cards may benefit from new drivers, but may also hit undiscovered bugs. Ubuntu 10.10 provides the 260.19.06 driver, so it would make sense upgrading it if your card is not supported.

---

### Post by Dorakara on 2011-03-30
well my card is supported in the additional driver menu and works well on that driver but I am unsure if any games through running wine may ask me to upgrade the drivers or such

---

