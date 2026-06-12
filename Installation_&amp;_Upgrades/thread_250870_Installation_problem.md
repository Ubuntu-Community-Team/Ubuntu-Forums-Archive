---
title: "Installation problem"
date: 2006-09-04
forum: Installation &amp; Upgrades
---

### Post by timbounceback on 2006-09-04
I was trying to upgrade to Ubuntu 6.06 from 5.10. However, at a point of the upgrade process it gives me this message:
Could not calculate the upgrade

An unresolvable problem occured while calculating the upgrade. Please report this as a bug.

I have attached a copy of my /var/log/dist-upgrade.log.

Thanks in advance!

---

### Post by Stone123 on 2006-09-04
I am guessing you haven't changed to or included all dapper mirrors.

---

### Post by timbounceback on 2006-09-04
Could you be more specific? On an unrelated note: The installation log says something about the file "ubuntu-desktop" and meta-packages.

---

### Post by Stone123 on 2006-09-04
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)


In Add channel window .check all , press custom button . and change breezy to dapper.  

Or you could open terminal and type :
sudo sed -ie 's/breezy/dapper/g' /etc/apt/sources.list && sudo apt-get update && sudo apt-get dist-upgrade

Btw there is this upgade tool that i woulden't recomend since it faild on  my system and it should be automatic.

---

### Post by timbounceback on 2006-09-05
Nope, that didn't work either - check the logfiles - it is the same error it gives me when I try installing manually.

---

### Post by DaveNF2G on 2006-09-30
It's not as simple as checking the right repositories.

There has always been a problem with 6.06 LTS distribution.

I have installed it before and had it working.  I cannot install it now.

My installation path is Breezy CD then upgrade to Dapper.  Why?  Because the files that are labeled as Dapper install images are PC-DOS v7 images, that's why. There is no Linux in those ISO files!  

So, when I have installed Dapper previously (this would be my third time), I have had to install Breezy first, then do an online update.

This time, the online update fails with the "Cannot calculate the upgrade" error that has been reported here numerous times, as well as in Dapper Morgan (or something) several months ago.  The last comment over there was "I'll look into it now" - as of JULY!!!

So, when will this problem / these problems get fixed!  Should I just abandon Ubuntu and go to another distro?

---

