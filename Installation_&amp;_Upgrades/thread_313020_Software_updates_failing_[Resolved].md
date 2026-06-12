---
title: "Software updates failing [Resolved]"
date: 2006-12-05
forum: Installation &amp; Upgrades
---

### Post by pinkpajamafairy on 2006-12-05
Ive been using ubuntu dapper for about 6months and until now ive had no problems with the update manager until the last week, and now its giving me error messages for some packages when i try to update.


```
 W: Failed to fetch http://nz.archive.ubuntu.com/ubuntu/pool/main/libr/libraw1394/libraw1394-8_1.2.1-2build1~dapper1_i386.deb
  404 Not Found


W: Failed to fetch http://nz.archive.ubuntu.com/ubuntu/pool/main/libr/libraw1394/libraw1394-dev_1.2.1-2build1~dapper1_i386.deb
  404 Not Found


W: Failed to fetch http://nz.archive.ubuntu.com/ubuntu/pool/main/l/lirc/liblircclient0_0.8.0-9ubuntu1~dapper1_i386.deb
  404 Not Found

```

is there any other way i can update these 3? or even just remove them from the update list so im not getting errors everytime i update? 

thanks!

---

### Post by d3v1ant_0n3 on 2006-12-05
You could always go to the repos [ manually](http://nz.archive.ubuntu.com/ubuntu/pool/main/libr/libraw1394/) ,download and install the correct debs for your architecture? I think that'd work?

---

### Post by ypout on 2006-12-06
I have the same issue with the nz.archive.ubuntu.com/ubuntu/pool/main/l/lirc/liblircclient0_0.8.0-9ubuntu1~dapper1_i386.deb

I looked at the URL and there is no file of that name in the lirc folder. The closest is called liblircclient0_0.8.0-9ubuntu1_i386.deb but when I tried to manually install the deb I got dependency errors, so I gave up.

It would be good to get this sorted... help:(

---

### Post by pinkpajamafairy on 2006-12-07
I tried again today using update manager (doing it manually is just slightly too complicated for me!) and it worked. Yay! :)

Thanks to whoever fixed it (im assuming someone did :p)

---

