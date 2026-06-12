---
title: "wireless driver (convert .exe to .inf)"
date: 2011-03-12
forum: Installation &amp; Upgrades
---

### Post by amal_matruk on 2011-03-12
hello;
i need your help  in an issue for linux. i have ubuntu  10.04 but i can not access wireless connection because it is disabled.  the soution for this is to add the windows wireless driver as you will  see in this video. but the problem is i only have it as (.exe) and it  should be (.inf)
[http://www.youtube.com/watch?v=m03RcFkSIA8](http://www.youtube.com/watch?v=m03RcFkSIA8)

do you know how can i convert this wireless driver from .exe to .inf so linux can accept it?

thanks again.

---

### Post by mörgæs on 2011-03-13
Hi, welcome to the fora.

Have you searched the manufacturer's web site? Could be that you can download drives there. [www.treiber-archiv.com](www.treiber-archiv.com) is another option.

What is in the .exe file? Might be a compressed file containing the drivers you need.

---

### Post by kagerato on 2011-03-13
The executable is probably a setup or other installer package.  You'd need to extract the actual Windows driver files (INF and others) from it.  Typically, in the process of running such an installer it unpacks the required files to a temporary directory, and that would be the place to look.

Sometimes the EXE is a self-extracting archive (an executable with a ZIP file or similar appended to it).  In those cases you can extract the contents using archive tools (such as 7-zip).

More importantly, though, you didn't mention what wireless device this is.  Most wireless cards have a native driver, and using one would be far more optimal than trying to hack together solutions based on ndiswrapper.

---

### Post by amal_matruk on 2011-03-14
thank you all,
I installed the wireless driver in Ubuntu and i extract it but it did not work. my version was 10.04 so i tried to reinstall Ubuntu and now i have 10.10 and it works good and now i can access INTERNET through wireless.

can the problem be that Ubuntu 10.04 has a problem with the wireless?

---

### Post by mörgæs on 2011-03-14
Good, please mark the thread 'solved'.

10.04 does not have a problem with wireless in general, but there could be some cards which are not supported well. 

Hardware support is normally increasing in the new versions (except for very old hardware, which might be considered obsolete).

---

