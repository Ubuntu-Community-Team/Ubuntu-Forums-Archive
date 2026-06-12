---
title: "How to get Floola working on 64 bit Jaunty"
date: 2009-02-15
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by cesera on 2009-02-15
I have had a bit of a look around on the internet on howto get Floola working on 64-bit ubuntu, and finally managed it with the help of [this post]("http://www.floola.com/modules/newbb/viewtopic.php?topic_id=834&forum=1") I basically just had to add one line to it to get Floola working. (Not 100% sure about playback as I don't normally use that.)
 
Download and install: [getlibs]("http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb")
Download Floola-linux.tar.gz
Open konsole. find your download and run the following commands:
```
tar zxvf Floola-linux.tar.gz
cd Floola-linux
getlibs ./Floola
getlibs -p gstreamer0.10-alsa
getlibs -p libgstreamer0.10-0
getlibs -p libgstreamer-plugins-base0.10-0
getlibs -p gstreamer0.10-plugins-ugly
getlibs -l libmad.so.0 libmpeg2.so.0 libdvdread.so.3 liboil-0.3.so.0 libsidplay.so
getlibs -l libid3tag.so.0 libcdio.so.7 libsidplay.so.1 liba52-0.7.4.so libdvdread.so.4
```
 
Hope this helps someone.

---

### Post by sephiroth_4 on 2009-04-13
Floola works, but everything is grayed out on my install.  I even tried these steps..but it was working before I did these steps anyway (Floola the program launches, but everything is still grayed out).

---

### Post by Floola on 2009-04-14
If everything is grayed out it means your iPod is not correctly mounted under /media or /mnt or you're expecting Floola to work with iPod touch or iPhones which unfortunately is not the case.


Tomas

---

