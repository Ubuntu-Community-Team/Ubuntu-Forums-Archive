---
title: "ipod and gtk applications"
date: 2009-10-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by dentaku65 on 2009-10-13
Hi all,
I've noted that my ipod (nano 3rd silver 4gb) is mounted correctly and I can browse it from nautilus, but I cannot managed in any way from the media applications; I've tried:
gtkpod
hipo
exaile
banshee
Simply the device is not viewed (does not exist for the applications). The only way that I found to use my ipod was to install the old version of Amarok 1.4 (PPA for Jaunty) 
[https://edge.launchpad.net/~bogdanb/+archive/amarok14/](https://edge.launchpad.net/~bogdanb/+archive/amarok14/)
and everything works perfect.
Does anybody else have the same issue, same model and same problem with gtk applications?

---

### Post by soapytheclown on 2009-10-13
After using amarok 1.4 does your ipod continue to function correctly? The reason I ask is that I've just this morning used amarok2 and its screwed up my xml somehow- it seems to be read fine in amarok2 but the ipod itself reports it has no music. Which is real kick in the balls! Most boring journey to work ever

---

### Post by dentaku65 on 2009-10-13
> **soapytheclown said:**
> After using amarok 1.4 does your ipod continue to function correctly? The reason I ask is that I've just this morning used amarok2 and its screwed up my xml somehow- it seems to be read fine in amarok2 but the ipod itself reports it has no music. Which is real kick in the balls! Most boring journey to work ever

Yes, it works really nice; did not tried with amarok 2 because I really dislike that app version.
I have some ideas that with gtk there is something wrong with hal and ipod (or at least with my model); in fact if I execute
```
podsleuth
```
command with ipod mounted I get
```
No iPods were found in the HAL device tree
```

:confused:

---

### Post by vaskark on 2009-10-13
I'm having the same prob.

```
xxxxx@karmic:~$ podsleuth
Found an iPod device, but it is not known by PodSleuth:
   Error: org.podsleuth.* properties are missing
   UDI:          /org/freedesktop/Hal/devices/volume_uuid_FE82_C3F8
   Block Device: /dev/sdb2
   Mount Point:  /media/IPOD NANO

   Cause: PodSleuth may not be installed properly, the HAL daemon may need
          to be restarted and/or the device needs to be refreshed.
```It recognized my ipod fine when I was using jaunty. However, Rhythmbox can find and play my ipod just fine, but Banshee (my preferred player) can't.

---

### Post by dentaku65 on 2009-10-13
I filled a bug here:
[https://bugs.launchpad.net/ubuntu/+source/hal/+bug/450465](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/450465)

---

### Post by Namain on 2009-10-13
I'm getting this same bug as well.  I've got an iPod Video 30 GB and previous to upgrading to Karmic, it was mounting as a 30 GB volume with the name of the iPod as the name of the volume.  Now it's mounting with the name "iPod", but HAL will not recognize is as such.

Any ideas out there?

---

