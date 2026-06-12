---
title: "gdm, kdm, xdm. A bug maybe?"
date: 2005-10-18
forum: Installation &amp; Upgrades
---

### Post by voger on 2005-10-18
I have installed ubuntu hoary and after that upgraded to kubuntu breezy with 
sudo apt-get dist-upgrade. The upgrade went fine with a little manual help and now i am enjoying my new box. 

        However i noticed something. When i tried to swich from gdm to kdm it went fine. Tried to switch to xdm and after changing to init 1 and back to init 2 i got no X windows. I did a sudo dpkg-reconfigure kdm to change back to kdm and after switching runlevels... still no X windows.  Anyway i was able to run kdm from command line.

         The solution i found was to run sudo dpkg-reconfigure kdm (or gdm) and select 
gdm, and after that again sudo dpkg-reconfigure kdm and select this time kdm.

         So everything works fine now. I am just wondering if anyone else has experienced this.

---

