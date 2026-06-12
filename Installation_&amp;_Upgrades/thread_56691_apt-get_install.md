---
title: "apt-get install"
date: 2005-08-13
forum: Installation &amp; Upgrades
---

### Post by speedemonV12 on 2005-08-13
i am having a hard time with this...whenever i try to do this, It always says that it cannot find the file. ....like apt-get install amarok     or    apt-get install amarok-xine. those are the two latest that dont work...but there are many more that do not work when i do this apt-get 

anyone know why?

thanks
speedy

---

### Post by lakcaj on 2005-08-13
Try the following, then post back if you are still having issues

apt-get update
apt-cache search amarok (make sure the package is actually there)
apt-get install amarok

---

### Post by speedemonV12 on 2005-08-13
Reading package lists... Done
Building dependency tree... Done
Package amarok is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package amarok has no installation candidate


it did not work for me...

---

### Post by lakcaj on 2005-08-13
It is working, it is saying it is not there.  Did you read the output from:

apt-cache search amarok

Did it show an amarok package?  I'm not on an ubuntu machine, but you can only install what apt-cache search shows is there.  What shows up when you search for amarok?

---

### Post by speedemonV12 on 2005-08-13
its okay i firgured it out in the end

---

### Post by speedemonV12 on 2005-08-13
Package amarok is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source



this is what happens when i try   apt-get install amarok....what does this mean 

what to i do ?

---

### Post by dbeckham32 on 2005-08-13
Make sure you have added to the /etc/apt/sources.list file; see the Starter Guide for more information:

[http://ubuntuguide.org/](http://ubuntuguide.org/)

---

