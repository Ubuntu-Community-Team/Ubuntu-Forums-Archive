---
title: "tryed to upgrade adobe flash deb"
date: 2009-10-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by suoko on 2009-10-23
and now i'm stuck with a non working synaptic
how to force things ?
dpkg -r --force neither works

---

### Post by dresden on 2009-10-23
same problem here with adobe-flashplugin
> 
Get:1 [http://archive.canonical.com](http://archive.canonical.com) karmic/partner adobe-flashplugin 10.0.32.18-1karmic1 [4,018kB]
Fetched 4,018kB in 20s (200kB/s)                                               
(Reading database ... 125506 files and directories currently installed.)
Preparing to replace adobe-flashplugin 10.0.22.87-2jaunty1 (using .../adobe-flashplugin_10.0.32.18-1karmic1_i386.deb) ...
update-alternatives: error: no alternatives for iceape-flashplugin.
update-alternatives: error: no alternatives for iceape-flashplugin.
dpkg: warning: old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
update-alternatives: error: no alternatives for iceape-flashplugin.
update-alternatives: error: no alternatives for iceape-flashplugin.
dpkg: error processing /var/cache/apt/archives/adobe-flashplugin_10.0.32.18-1karmic1_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 2
postinst called with argument `abort-upgrade'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/adobe-flashplugin_10.0.32.18-1karmic1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by go7Ul1ai on 2009-10-23
+1

---

### Post by sports fan Matt on 2009-10-23
Mine is just greyed out.

---

### Post by zeronothing on 2009-10-23
I too am having this problem. In synaptic you can't even select to "Completely remove" because it says "Package is in a very bad inconsistent state." something has definitely freaked out in the latest update.

---

### Post by Tharna on 2009-10-23
I managed to solve it by:
1. Comment out everything in /var/lib/dpkg/info/adobe-flashplugin.prerm 
2. Remove flashplugin: sudo dpkg -r --force-all adobe-flashplugin
3. Install flashplugin with your preferred method normally.

---

### Post by philinux on 2009-10-23
I guess all you guys are on 32 bit?

---

### Post by habtool on 2009-10-23
I am on 32 Bit

---

### Post by zeronothing on 2009-10-23
Yes, I'm on 32-bit as well

---

### Post by zeronothing on 2009-10-23
Thanks Tharna for your help. Your steps you provided helped clean up my issue with adobe-flashplugin. After I followed your steps I just reinstalled the flashplugin from the "Ubuntu Software Center" and it now works.

---

### Post by kansasnoob on 2009-10-23
> **Tharna said:**
> I managed to solve it by:
1. Comment out everything in /var/lib/dpkg/info/adobe-flashplugin.prerm 
2. Remove flashplugin: sudo dpkg -r --force-all adobe-flashplugin
3. Install flashplugin with your preferred method normally.

Thanks, that worked!

---

### Post by linusr on 2009-10-23
> **Tharna said:**
> I managed to solve it by:
1. Comment out everything in /var/lib/dpkg/info/adobe-flashplugin.prerm 
2. Remove flashplugin: sudo dpkg -r --force-all adobe-flashplugin
3. Install flashplugin with your preferred method normally.

Thanks, it worked.

wondering why was adobe's version of flash removed from repo?

---

### Post by hazahel on 2009-10-23
> **Tharna said:**
> I managed to solve it by:
1. Comment out everything in /var/lib/dpkg/info/adobe-flashplugin.prerm 
2. Remove flashplugin: sudo dpkg -r --force-all adobe-flashplugin
3. Install flashplugin with your preferred method normally.

Thanks for your help, it worked !

---

### Post by sports fan Matt on 2009-10-23
32 bit here as well

---

### Post by UNOwen on 2009-10-23
> 1. Comment out everything in /var/lib/dpkg/info/adobe-flashplugin.prerm
2. Remove flashplugin: sudo dpkg -r --force-all adobe-flashplugin
3. Install flashplugin with your preferred method normally.


I also have to thank Tharna. Your three steps worked like a charm. :KS

---

### Post by Nokia on 2009-10-24
Thanks. It worked on one PC, but it didn't on the second one. I still get ```


sudo dpkg -r adobe-flashplugin --force-all
dpkg: error processing adobe-flashplugin (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
dpkg: warning: ignoring request to remove --force-all which isn't installed.
Errors were encountered while processing:
 adobe-flashplugin
```

I recheck everything and there's no error on my part.

---

### Post by Nokia on 2009-10-24
Solved it by temporarily reverting to Jaunty's sources and reinstalling the package. Now waiting for karmic's version.

---

