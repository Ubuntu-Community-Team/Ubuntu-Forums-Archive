---
title: "Kernel headers, 2.6.31-11-generic -- do you have them?"
date: 2009-09-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by dabl on 2009-09-28
System is Kubuntu:
```

dabl@karmic:~$ uname -a
Linux karmic 2.6.31-11-generic #36-Ubuntu SMP Fri Sep 25 06:37:23 UTC 2009 x86_64 GNU/Linux
dabl@karmic:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu karmic (development branch)
Release:        9.10
Codename:       karmic
```

```
dabl@karmic:~$ sudo apt-get install linux-headers-$(uname -r)
Reading package lists... Done
Building dependency tree
Reading state information... Done
linux-headers-2.6.31-11-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```


VMware Player 2.5.3, 64-bit, says "Kernel headers for version 2.6.31-11-generic were not found" blah blah blah.  I pointed it to the /usr/src/linux-headers-2.6.31-11-generic directory (but it was already looking there), but it says there are no header files there.

It built and ran fine on the preceding kernel.

Anyone else seeing this?

---

### Post by kansasnoob on 2009-09-28
> **dabl said:**
> System is Kubuntu:
```

dabl@karmic:~$ uname -a
Linux karmic 2.6.31-11-generic #36-Ubuntu SMP Fri Sep 25 06:37:23 UTC 2009 x86_64 GNU/Linux
dabl@karmic:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu karmic (development branch)
Release:        9.10
Codename:       karmic
```

```
dabl@karmic:~$ sudo apt-get install linux-headers-$(uname -r)
Reading package lists... Done
Building dependency tree
Reading state information... Done
linux-headers-2.6.31-11-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```


VMware Player 2.5.3, 64-bit, says "Kernel headers for version 2.6.31-11-generic were not found" blah blah blah.  I pointed it to the /usr/src/linux-headers-2.6.31-11-generic directory (but it was already looking there), but it says there are no header files there.

It built and ran fine on the preceding kernel.

Anyone else seeing this?

Straight Ubuntu here:

> lance@lance-desktop:~$ cat /etc/issue
Ubuntu karmic (development branch) \n \l


> lance@lance-desktop:~$ apt-cache showpkg vlc
Package: vlc
Versions: 
1.0.2-1ubuntu1 (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_karmic_universe_binary-i386_Packages) (/var/lib/dpkg/status)
 Description Language: 
                 File: /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_karmic_universe_binary-i386_Packages
                  MD5: 2e285259e2f85da8440dcf1707050a98


Reverse Depends: 
  mythbuntu-desktop,vlc
  ltsp-controlaula,vlc
  freeplayer,vlc 0.8.6b
  controlaula,vlc
  vlc-nox,vlc 0.9.8a-3
  vlc-nox,vlc 0.9.8a-3
  tunapie,vlc
  remuco-vlc,vlc 0.9
  pidgin-mpris,vlc
  peercast-handlers,vlc
  mozilla-plugin-vlc,vlc
  libvlc2,vlc 0.8.6.c-6
  libvlc2,vlc 0.8.6.c-6
  kamoso,vlc
  gaupol,vlc
Dependencies: 
1.0.2-1ubuntu1 - vlc-nox (5 1.0.2-1ubuntu1) libaa1 (2 1.4p5) libc6 (2 2.8) libdbus-1-3 (2 1.0.2) libfreetype6 (2 2.2.1) libfribidi0 (2 0.10.9) libgcc1 (2 1:4.1.1) libgl1-mesa-glx (16 (null)) libgl1 (0 (null)) libglib2.0-0 (2 2.12.0) libgtk2.0-0 (2 2.8.0) libnotify1 (2 0.4.5) libnotify1-gtk2.10 (0 (null)) libqtcore4 (2 4.5.1) libqtgui4 (2 4.5.1) libsdl-image1.2 (2 1.2.5) libsdl1.2debian (2 1.2.10-1) libstdc++6 (2 4.2.1) libtar (0 (null)) libvlccore2 (2 1.0.0~rc1) libx11-6 (0 (null)) libx264-67 (2 1:0.svn20090502) libxext6 (0 (null)) libxinerama1 (0 (null)) libxv1 (0 (null)) libxxf86vm1 (0 (null)) zlib1g (2 1:1.2.3.3.dfsg) ttf-dejavu-core (0 (null)) mozilla-plugin-vlc (0 (null)) videolan-doc (0 (null)) vlc-plugin-pulse (5 1.0.2-1ubuntu1) vlc-nox (3 0.9.2-1) vlc-nox (3 0.9.2-1) 
Provides: 
1.0.2-1ubuntu1 - mp3-decoder 


EDIT: Soory VMware turned into VLC in my noggen!!!!!!!!

---

### Post by darco on 2009-09-28
> **dabl said:**
> System is Kubuntu:
```

dabl@karmic:~$ uname -a
Linux karmic 2.6.31-11-generic #36-Ubuntu SMP Fri Sep 25 06:37:23 UTC 2009 x86_64 GNU/Linux
dabl@karmic:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu karmic (development branch)
Release:        9.10
Codename:       karmic
```

```
dabl@karmic:~$ sudo apt-get install linux-headers-$(uname -r)
Reading package lists... Done
Building dependency tree
Reading state information... Done
linux-headers-2.6.31-11-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```


VMware Player 2.5.3, 64-bit, says "Kernel headers for version 2.6.31-11-generic were not found" blah blah blah.  I pointed it to the /usr/src/linux-headers-2.6.31-11-generic directory (but it was already looking there), but it says there are no header files there.

It built and ran fine on the preceding kernel.

Anyone else seeing this?

Did you get the .31.11 from the KK repo's?

darco

---

### Post by ayates on 2009-09-29
2.5.3 built and runs fine here, but I am 32 bit.

---

### Post by seanmcneil3 on 2009-09-29
I had the same problem. It is because you added a hack (like me) to get around the focus issue. You need to uncomment that hack and run vmplayer again to have it make the kernel modules. Once done, put the hack back in. The hack is:

export VMWARE_USE_SHIPPED_GTK=force

So, comment out, run, then comment back in.

Cheers!

---

### Post by dabl on 2009-09-29
> **seanmcneil3 said:**
> I had the same problem. It is because you added a hack (like me) to get around the focus issue.

Ahhh Sean, you are a genius -- thank you my friend!  That is indeed the problem -- I had no idea that hack affected the kernel headers "reading".  This one is SOLVED.  :guitar:

---

