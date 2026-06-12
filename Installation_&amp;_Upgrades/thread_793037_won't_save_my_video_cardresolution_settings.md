---
title: "won't save my video card/resolution settings"
date: 2008-05-13
forum: Installation &amp; Upgrades
---

### Post by ntyhurst on 2008-05-13
complete noob at all this so please bear with me.  i installed the most recent version of Ubuntu, downloaded and installed the updates.  now when i boot it tells me that it will have to boot in safe graphics mode so i run:

sudo dpkg-reconfigure xserver-xorg

and set it all up and then it will work nicely.  but every time i reboot i have to go through the whole dpkg-reconfigure process again to set it up.  

i did sudo nvidia-settings

and saved the changes to xorg.conf but its still reverting to safe graphics mode.  


oh yeah and i forgot to mention that doing the dpkg-reconfigure doesn't always work.  maybe like every 3rd time it will work, otherwise it goes right back to safe graphics mode
help...please

---

### Post by borlosky on 2008-05-17
having same issue after upgrading to 8.04 from 7.10, tried uninstalling/reinstalling nvidia drivers, pc will work after reboot after reinstalling the drivers, but once i reboot again, then issue starts all over. again, this has only started since upgrading to 8.04 FROM 7.10

---

### Post by ntyhurst on 2008-05-17
yeah, exactly.  i just haven't been using the OS since its a huge hassle to go through that every time.  if anyone out there has any idea...?

---

### Post by Pumalite on 2008-05-17
Check 'uname -a' againts menu.lst.

---

### Post by borlosky on 2008-06-28
> **borlosky said:**
> having same issue after upgrading to 8.04 from 7.10, tried uninstalling/reinstalling nvidia drivers, pc will work after reboot after reinstalling the drivers, but once i reboot again, then issue starts all over. again, this has only started since upgrading to 8.04 FROM 7.10

found the problem, apparently, the drivers didn't work anymore with my geforce 5700 ultra card for whatever reason, I was able to get a geforce 6200 from a friend, and now everything works fine :guitar:

---

