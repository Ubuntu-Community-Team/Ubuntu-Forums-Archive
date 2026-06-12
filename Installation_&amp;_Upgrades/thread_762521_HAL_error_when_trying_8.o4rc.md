---
title: "HAL error when trying 8.o4rc"
date: 2008-04-22
forum: Installation &amp; Upgrades
---

### Post by drsox1899 on 2008-04-22
I have 2 PCs - one for use and one for playing about.  I burnt a CD of the 8.04rc (no errors etc).  It runs on the "use" PC but not on the "playing about" PC.

I get an error message - HAL failed to initialise.  After that not much works.

Any solution to this or is there some fundamental incompatibility with my setup ?  Ubuntu 7.10 runs just fine on this PC.

It's an AMD BE-2300 on an Asrock ALiveNF6P-VSTA with an NVidia 7300 card.

---

### Post by wpshooter on 2008-04-22
Why don't you report it as a bug to see if someone might come up with a solution and further improve the Hardy version.

---

### Post by drsox1899 on 2008-04-22
Thanks.  How do I do that ?

OK.  I found it in Launchpad.

---

### Post by jmore9 on 2008-04-22
Hello !

I went and decided to do a distro upgrade by clicking on the distro upgrade button on the software updater wizard.  After 40 minutes of downloading and 30 on installing the machine wanted to reboot so i rebooted.  Upon reboot i got hte following error/s:

1. internal error -- hal cannot be found

2. internal error -- hal cannot be initialized

3. some type of warning about low battery .
   -- my machine is a desktop does not have a battery --
   -- i am still looking for the battery that hardy upgrade found -

4. I am assuming that if the hal interface is not working properly then items that it controls will not work properly. Such as the network card.  It deleted everything but the wireless connection that it found :(

   I don't have a wireless connection.  I tried all night to restore the Ethernet card and the internet but was not able to so i just formated and reinstalled ubuntu 7.10.  Also the sound card -- a soundblaster 64 -- was lost and it was using device null -- i was having a hard time listening to my music via device null !!!
 
I guess i will wait until the final release is out before i try to upgrade again , this time complete reinstall

---

### Post by drsox1899 on 2008-04-23
> **jmore9 said:**
> Hello !

I went and decided to do a distro upgrade by clicking on the distro upgrade button on the software updater wizard.  After 40 minutes of downloading and 30 on installing the machine wanted to reboot so i rebooted.  Upon reboot i got hte following error/s:

1. internal error -- hal cannot be found

2. internal error -- hal cannot be initialized

3. some type of warning about low battery .
   -- my machine is a desktop does not have a battery --
   -- i am still looking for the battery that hardy upgrade found -

4. I am assuming that if the hal interface is not working properly then items that it controls will not work properly. Such as the network card.  It deleted everything but the wireless connection that it found :(

   I don't have a wireless connection.  I tried all night to restore the Ethernet card and the internet but was not able to so i just formated and reinstalled ubuntu 7.10.  Also the sound card -- a soundblaster 64 -- was lost and it was using device null -- i was having a hard time listening to my music via device null !!!
 
I guess i will wait until the final release is out before i try to upgrade again , this time complete reinstall

I'm sorry that you have the same problem but relieved that it isn't just me.  What mobo do you have ?  I also saw that it had lost my ethernet card + the mobo ethernet.  Fortunately I could revert to 7.10 without problems.  I have also tried installing Kubuntu 8.04 rc on the same PC - didn't want to install at all except in Live CD mode.

I have another old Laptop - I'll have a go with that.  On the Ubuntu 8.04 - the laptop installed but the screen was half the size !

---

### Post by drsox1899 on 2008-04-24
This problem is SOLVED with 8.04 release.  Have just installed it and not seen any problems !!

---

