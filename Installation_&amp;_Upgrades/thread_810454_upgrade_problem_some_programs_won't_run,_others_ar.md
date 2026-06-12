---
title: "upgrade problem: some programs won't run, others are fine"
date: 2008-05-28
forum: Installation &amp; Upgrades
---

### Post by Jeffa on 2008-05-28
Hello Community, 

I just upgraded to 8.04 yesterday. The upgrade process went fine, no errors or anything. 

but after using ubuntu for a while, i've noticed some programs won't start. Specifically, if i try and run 

System->Administration->
  Samba
  Firestarter
  Hardware Testing
  Software Sources
  Synaptec Package Manager 
  Update Manager

I get a little box at the bottom of the screen saying the package is starting, but then the box disappears and the package never starts. I also can't seem to install packages through "Applications->Add/Remove" 

I'm running the 64 bit version. 

I searched around these forums, but didn't really see any other issues like this. 


any help would be appreciated. 

thanks

---

### Post by hal8000 on 2008-05-28
> **Jeffa said:**
> Hello Community, 

I just upgraded to 8.04 yesterday. The upgrade process went fine, no errors or anything. 

but after using ubuntu for a while, i've noticed some programs won't start. Specifically, if i try and run 

System->Administration->
  Samba
  Firestarter
  Hardware Testing
  Software Sources
  Synaptec Package Manager 
  Update Manager

I get a little box at the bottom of the screen saying the package is starting, but then the box disappears and the package never starts. I also can't seem to install packages through "Applications->Add/Remove" 

I'm running the 64 bit version. 

I searched around these forums, but didn't really see any other issues like this. 


any help would be appreciated. 

thanks


I'm not running 64bit version but you need to start each program from a terminal. Hopefully some useful output may be gained as to whats wrong.


For synaptic type

sudo synaptic

for hardware testing the command is:
gksu /usr/bin/hwtest-gtk


You can find out the command for each shortcut by rightclicking each item, add the launcher to desktop then check properties and launcher command that way.
Hope you find a solution.

---

### Post by dstew on 2008-05-28
Check [this thread]("http://ubuntuforums.org/archive/index.php/t-613521.html"). Apparently you get a line in your /etc/hosts file that causes the problem.

---

### Post by Jeffa on 2008-05-28
> **dstew said:**
> Check [this thread]("http://ubuntuforums.org/archive/index.php/t-613521.html"). Apparently you get a line in your /etc/hosts file that causes the problem.

Brilliant! That did the trick. You sir have earned yourself a "Thanks"! My only regret is that I have but one to give. 

Cheers.

---

