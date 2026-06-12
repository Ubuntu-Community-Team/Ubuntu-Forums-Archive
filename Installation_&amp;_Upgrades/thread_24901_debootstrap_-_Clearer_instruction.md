---
title: "debootstrap - Clearer instruction"
date: 2005-04-08
forum: Installation &amp; Upgrades
---

### Post by mpa on 2005-04-08
I think the instruction in /doc/install/manual/en/apcs04.html could be made clearer by changing the line in 

------------------------------------------------
C.4.3. Run debootstrap

debootstrap can download the needed files directly from the archive when you run it. You **can** substitute any Ubuntu archive mirror for archive.ubuntulinux.org/ubuntu in the command example below,

 $ /usr/sbin/debootstrap --arch ARCH hoary \
     /mnt/debinst [http://http.us.debian.org/debian](http://http.us.debian.org/debian)

------------------------------------------------
To :
------------------------------------------------

C.4.3. Run debootstrap

debootstrap can download the needed files directly from the archive when you run it. You **must** change "http.us.debian.org/debian" to any Ubuntu archive mirror.

 $ /usr/sbin/debootstrap --arch ARCH hoary \
     /mnt/debinst [http://http.us.debian.org/debian](http://http.us.debian.org/debian)

------------------------------------------------

I tried installing hoary and because it says "i can substitute" so I didnt, which results in :


root # usr/sbin/debootstrap --arch i386 hoary /mnt/debinst/ [http://http.us.debian.org/debian](http://http.us.debian.org/debian)
I: Retrieving debootstrap.invalid_dists_hoary_Release
E: Failed getting release file [http://http.us.debian.org/debian/dists/hoary/Release](http://http.us.debian.org/debian/dists/hoary/Release)

which confused me for quite a while :-)

---

