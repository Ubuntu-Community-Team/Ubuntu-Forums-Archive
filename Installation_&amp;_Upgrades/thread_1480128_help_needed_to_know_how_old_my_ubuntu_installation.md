---
title: "help needed to know how old my ubuntu installation is"
date: 2010-05-11
forum: Installation &amp; Upgrades
---

### Post by Budhraj on 2010-05-11
Hi 

&#65279;If ubuntu installation is done on Feb 1 2010 on a  back date say Jan 1 2010, (by changing  date in BIOS )

Now on 2nd Feb  I change the system date to Actual date today that is 2nd Feb,  how can we  know the correct  date or time of installation or how many days back the installation was done.

---

### Post by kingneutron on 2010-05-12
> **Budhraj said:**
> Hi 

&#65279;[SIZE=3]If ubuntu installation is done on Feb 1 2010 on a  back date say Jan 1 2010, (by changing  date in BIOS )

Now on 2nd Feb  I change the system date to Actual date today that is 2nd Feb,  how can we  know the correct  date or time of installation or how many days back the installation was done.[/SIZE]
--My recommendation would be to create a local install logfile - I use /root/localinfo.txt or similar, and make a note of when the system was installed.

root ~ # head localinfo.txt
2009.0808 + Installed Ubuntu 8.04.3--64 LTS on sda1

--If the dates and times on the install files mean a lot, you might want to actually re-do the install with the correct date/time set on the PC.

---

### Post by kingneutron on 2010-05-12
> **Budhraj said:**
> Hi 

&#65279;[SIZE=3]If ubuntu installation is done on Feb 1 2010 on a  back date say Jan 1 2010, (by changing  date in BIOS )

Now on 2nd Feb  I change the system date to Actual date today that is 2nd Feb,  how can we  know the correct  date or time of installation or how many days back the installation was done.[/SIZE]
--My recommendation would be to create a local install logfile - I use /root/localinfo.txt or similar, and make a note of when the system was installed.

root ~ # head localinfo.txt
2009.0808 + Installed Ubuntu 8.04.3--64 LTS on sda1

--If the dates and times on the install files mean a lot, you might want to actually re-do the install with the correct date/time set on the PC.

---

### Post by Budhraj on 2010-05-12
thanks for reply 

but i didn't created any log file ,   any other way

---

