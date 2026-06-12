---
title: "No sound in 9.10, Place Help.."
date: 2009-11-28
forum: Installation &amp; Upgrades
---

### Post by dayan.rj on 2009-11-28
Hello..
 
I'm new to Ubuntu and i upgraded to 9.10. And i had some sound trouble, it kept going off when ever i rested the pc. but ones i make the volume high it worked. my sound card is a "**realtek AC97**"

Then i tried to install the downloaded files from the realtek site with the help of there Reademe.

------------------------------------------------------------------------------------------------------
Manual install:
Step 1. unzip source code
        tar xfvj alsa-driver-1.0.xx.tar.bz2

Step 2. Turn on sound support (soundcore module, default turn on)

Step 3. Complied source code
    a. cd alsa-driver-1.0.xx
    b. ./configure
    c. make
    d. make install
    e. ./snddevices
--------------------------------------------------------------------------------------------------------

***i got an error in the end, now i cant hear any thing at all**. **plz help me some one.**

---

### Post by tommcd on 2009-11-28
> **dayan.rj said:**
> 
I'm new to Ubuntu and i upgraded to 9.10. And i had some sound trouble, it kept going off when ever i rested the pc. but ones i make the volume high it worked. my sound card is a "**realtek AC97**"

What does "rested the pc" mean? If the sound works when you turn the volume up, then it is working. Run **alsamixer** in the terminal and move all the volume levels up and try the sound.
Beyond that, you can try working your way through the sound troubleshooting guide:
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
> **dayan.rj said:**
> 
Then i tried to install the downloaded files from the realtek site with the help of there Reademe.

I would not use the driver from Realtek. You probably have the driver running already if you get sound with the volume turned up.

---

### Post by dayan.rj on 2009-11-30
Sorry my spellings are not that good... :) i met as "**restart the pc**".
was able to reinstall the default driver that comes with ubunthu with the help of the [B]sound troubleshooting guide.
[/B]And use the Alsamixer to put the volume up.. Now it works fine, Thanks 2 you.. :)

Thanks again for your kind help..

---

