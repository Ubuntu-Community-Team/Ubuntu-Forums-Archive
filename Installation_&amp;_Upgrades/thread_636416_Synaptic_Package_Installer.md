---
title: "Synaptic Package Installer"
date: 2007-12-09
forum: Installation &amp; Upgrades
---

### Post by Ryan123004 on 2007-12-09
Hi,
I've been using Ubuntu for a couple of weeks now and all of a sudden "Synaptic Package Installer" began showing this error:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Please help me fix this.

Thanks,
Ryan

---

### Post by Joeb454 on 2007-12-09
open up a terminal (Applications > Accessories > Terminal)

and then type ```
sudo dpkg --configure -a
```

That should sort it, try it and post back :)

---

### Post by Ryan123004 on 2007-12-10
ok i typed that in and it says:

Password: 

i tried typing it in but it wont show any charachters i type

---

### Post by Partyboi2 on 2007-12-10
it wont show anything as you type.

---

### Post by Ryan123004 on 2007-12-10
oh man. i got it.
now i think i'm back to what caused the problem
when i open synaptic it says:

You have 1 broken package on your system!
Use the "Broken" filter to locate it.

any suggestions?

---

### Post by Partyboi2 on 2007-12-10
Open Synaptic (System>Amin>Synaptic Package Manager)
then select edit from menu
then fix broken package

---

### Post by Ryan123004 on 2007-12-10
oh wow thanks a lot

---

### Post by Partyboi2 on 2007-12-10
you should also be able to do it using
```
sudo apt-get install -f
```

---

