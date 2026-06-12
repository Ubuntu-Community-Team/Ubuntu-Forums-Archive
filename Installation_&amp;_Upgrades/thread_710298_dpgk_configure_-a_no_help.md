---
title: "dpgk configure -a no help"
date: 2008-02-28
forum: Installation &amp; Upgrades
---

### Post by dksau on 2008-02-28
attempted to install vmware have decided not to and don't have asked for serial number.  installation is hung up.  when attempting to upgrade or install anything else i get a warning to run dpgk configure -a which i have tried but it doesn't help.  currently can't install anything including updates

---

### Post by taurus on 2008-02-28
You mean you have ran these?

```
sudo dpkg --configure -a
sudo apt-get update
```

---

### Post by dksau on 2008-02-28
I tried this and it still comes to the same end I get a screen asking for a serial number and an ok or cancel button which do not work.  I have decided I don't want the vmware but can't halt the process:(

---

### Post by dksau on 2008-02-28
I tried this again and if finally did come up with another window and finished up to the configuration point and then I had a usable opportunity to cancel.:) thank you:)

---

### Post by dksau on 2008-02-28
I was able to stop the configuration process but now everytime I try to install something I get a vmware screen asking for serial number or cancel which doesn't do anything. How do I get rid of that?:)

---

### Post by dksau on 2008-02-28
Im getting this message when accessing synaptic package manager

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by forestpixie on 2008-02-28
try running it```
sudo dpkg --configure -a
```

after you've done that use apt-get to remove vmware

```
sudo apt-get remove vmware
```

---

### Post by dksau on 2008-02-28
after using the above cammand sequence I still get part of the part of the unwanted vmware program and the installations stalls.  this thing is like a virus:(

---

