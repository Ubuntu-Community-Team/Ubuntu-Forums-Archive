---
title: "Need help!!!!!!!"
date: 2009-10-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by yamabushi334 on 2009-10-06
I have been doing dpkg for the last few days trying to get 9.10 to work but it has done nothing to help me yet. I complete the process of dpkg and after i install and reboot to try to get into ubuntu it says: MMC0: Unknown controller version 2. Then below that it says: B43-PHY0 Error: Found unsupported PHY (Analog 6, Type 5, Revision 1.) Then my screen starts flickering really bad and it lags so I can't log in even when I try it says incorrect log in. I have no idea on what these mean I would like to know what they mean and if they can be fixed.

---

### Post by sedawk on 2009-10-06
First dpkg is a low-level tool a normal user should not have
to bother with. To have an up-to-date system without
using the desktop you normally can rely on this:
```

apt-get update
apt-get update # only if the first one came up with an error
apt-get dist-upgrade

```

AFAIK "MMC0: Unknown controller version 2" means you have
a card reader but it reports a version the kernel doesn't
know about.
Similar problem with "B43-PHY0 Error: Found unsupported PHY (Analog 6, Type 5, Revision 1.)"
Your system detects a wireless device from Broadcom
but it doesn't know the revision of it.

Is is possible you are running on brand new hardware?
If the hardware is not working (I'm not sure the above
messages are errors or simply warnings) you have to 
wait for a newer kernel that supports it.
It is very unlikely that you suffer from missing packages
or obsolete packages.

Do you get a desktop when running the Live-CD of 9.04 or
the latest 9.10 (beta) Live-CD? There might be an issue
with your graphics card (again brand new?) so Ubuntu
fails to switch to the desktop. If the Live-CD works you
might be able to use the generic VESA driver as a fallback
solution.

You do not have problems with missing or obsolete

---

### Post by yamabushi334 on 2009-10-06
My graphics card is a legacy card now it is not supported by ATI anymore its a ATI raedon x1250. I did the distrobution update by doing update-manager -d when I was using 9.04. The only hardware I have recently updated on my laptop was my harddrive and my RAM. I will download the live CD of 9.10 later this evening and see if it will let me boot into it and then I will try installing it from that and see if that works out.

---

### Post by yamabushi334 on 2009-10-06
I am finally on ubuntu 9.10 had to reinstall it using the live cd it is running great and no more problems thanks to everyone who helped.

---

### Post by emarkay on 2009-10-06
Please mark this thread "Solved" then.  :)

---

