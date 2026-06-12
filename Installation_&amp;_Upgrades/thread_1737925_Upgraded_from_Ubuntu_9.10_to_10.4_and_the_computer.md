---
title: "Upgraded from Ubuntu 9.10 to 10.4 and the computer became slow"
date: 2011-04-24
forum: Installation &amp; Upgrades
---

### Post by Gyalogtank on 2011-04-24
I recently bought a Dell Inspiron 5010 laptop (AMD V160 processor, 2 gigabytes of RAM). It came with a factory installed Ubuntu 9.10 which was lightning fast. I upgraded to 10.4 using the update manager, and the system became irritatingly slow, to the point of being useless. I upgraded to 10.10, however the speed did not change, and even booting became problematic. I re-installed 9.10 from using the factory recovery partition and the system became fast once again. Then I upgraded to 10.4 and the system is still slow to the point of being useless. What can be the problem? How can I fix it?

---

### Post by earthpigg on 2011-04-24
For me with my dell system several years back, the Dell install was utter crap.

I did my own installation of plain normal vanilla Ubuntu myself, and things have worked beautifully on that computer ever since. 

In your shoes, I'd download a LiveCD .iso from ubuntu.com, burn it (or put it on USB), and try that.



(I have no idea why Dell thinks it is a good idea to fix what isn't broken.)

---

### Post by dino99 on 2011-04-24
little howto install:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by Gyalogtank on 2011-08-08
Hi, thanks for the help, after a fresh install the system was still slow. 

However disabling acpi (adding "acpi=off" to GRUB) solved the problem.

---

