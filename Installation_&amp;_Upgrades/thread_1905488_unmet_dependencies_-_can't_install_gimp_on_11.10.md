---
title: "unmet dependencies - can't install gimp on 11.10"
date: 2012-01-07
forum: Installation &amp; Upgrades
---

### Post by Jinch&#363;riki on 2012-01-07
running Ubuntu 11.10 64-bit

I can't seem to install GIMP after having uninstalled it in an effort to clear up various glitchy behavior which has been going on since the upgrade from 11.04 to 11.10

$ sudo apt-get install gimp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable distribution that some required packages have not yet been created or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gimp : Depends: gimp-data (<= 2.6.11-z) but 2.7.3-2011052002~nn is to be installed
E: Unable to correct problems, you have held broken packages.

I've read several related threads in the forums and tried cleaning and purging and re-installing to no avail.

Any thoughts?

Thanks, jin

---

### Post by lkraemer on 2012-01-07
You problem stems from the upgrade from 11.04 to 11.10.  It appears you have
also held broken packages, and you most likely need to fix those.  It should
be under SYNAPTICS -> EDIT -> FIX BROKEN PACKAGES 

To get around this you should look to see if gimp-data is installed, and if it is,
remove it as it is an older version ((<= 2.6.11-z) but 2.7.3-2011052002).
Then you can just open a terminal and install gimp-data.
```

sudo apt-get install gimp-data --force-yes

```
which should get the dependency installed.  Then just install gimp.
```

sudo apt-get install gimp

```
That should work.......

lk

---

### Post by Jinch&#363;riki on 2012-01-07
Thanks for the reply, I followed your instructions and gimp / gimp-data are seemingly installed correctly, however gimp will not launch:

$ gimp
gimp: error while loading shared libraries: libgegl-0.0.so.0: cannot open shared object file: No such file or directory

I'm looking through the forums now for details of this libgegl-

If you have any further insights I'd appreciate it.  I'll post again should I solve it in the meanwhile.

Thanks, jin

---

### Post by Jinch&#363;riki on 2012-01-07
I ended up uninstalling everything and following the lines here:

[http://www.noobslab.com/2011/09/install-gimp-27-on-ubuntu-1110-oneiric.html](http://www.noobslab.com/2011/09/install-gimp-27-on-ubuntu-1110-oneiric.html)

It's up and running!

Thanks for your help.  I had no idea Gimp was dropped from Ubuntu's standard desktop release.  

All the best, Jin

---

### Post by raja.genupula on 2012-01-08
Glad your issue solved please mark the thread as solved from thread tools . Thanks man.

---

### Post by Jinch&#363;riki on 2012-01-08
Done and done.. :)

Thanks!

---

