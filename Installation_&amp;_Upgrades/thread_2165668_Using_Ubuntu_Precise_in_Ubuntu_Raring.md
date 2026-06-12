---
title: "Using Ubuntu Precise in Ubuntu Raring"
date: 2013-08-05
forum: Installation &amp; Upgrades
---

### Post by Rishav_Kumar on 2013-08-05
I have ubuntu raring (13.04) installed on my computer. However, I have softwares(specifically ROS) that are not supported by ubuntu raring. ROS(fuerte desktop full version) runs on ubuntu precise at least.

Is there any way i can use ubuntu precise in ubuntu raring i.e. need not have to install ubuntu precise alongside ubuntu raring? Are there any virtual engines/machines (like the ones that allow using Windows XP in Windows 7) that can get me running ROS in raring?

Please suggest the best alternative.

---

### Post by Frogs Hair on 2013-08-05
See the link for one alternative. There may be some options in the software center also.  [https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)

---

### Post by Rishav_Kumar on 2013-08-06
Thank you.
Someone suggested to download the required libraries of the the precise version that works with the software and then use the software. Is that correct? In that way i would avoid the use of a virtual box. The main problem during installing the software in raring(not supported) is that there are broken packages that are not getting fixed. Is there any work around?

---

### Post by Frogs Hair on 2013-08-06
I don't know if  there is much you can do if there are conflicts causing broken packages . 12.04 uses gnome 3.4 libs and 13.04 uses 3.6 . Even If you found a W/O by compiling  a simple update may break it anyway. VBox. and similar software use a lot of memory so that is a consideration also .

---

