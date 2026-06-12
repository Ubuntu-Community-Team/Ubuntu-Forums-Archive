---
title: "unable to install bind9 on ubuntu 12.04"
date: 2013-10-09
forum: Installation &amp; Upgrades
---

### Post by jamesbon on 2013-10-09
I am getting error while trying to install bind9 on ubuntu 12.04 I did ```
sudo aptitude install bind9
```

following is snapshot of error [IMG]https://skydrive.live.com/redir?resid=3D83B0F74F998B69!165&authkey=!ABIfn-fR1b3WGNE&v=3[/IMG]
[http://sdrv.ms/1cvEtqX](http://sdrv.ms/1cvEtqX)
> 
The following NEW packages will be installed:
  bind9{b} 
0 packages upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 336 kB of archives. After unpacking 962 kB will be used.
The following packages have unmet dependencies:
 bind9 : Depends: libbind9-80 (= 1:9.8.1.dfsg.P1-4) but 1:9.8.1.dfsg.P1-4ubuntu0.5 is installed.
         Depends: libdns81 (= 1:9.8.1.dfsg.P1-4) but 1:9.8.1.dfsg.P1-4ubuntu0.5 is installed.
         Depends: libisc83 (= 1:9.8.1.dfsg.P1-4) but 1:9.8.1.dfsg.P1-4ubuntu0.5 is installed.
         Depends: libisccc80 (= 1:9.8.1.dfsg.P1-4) but 1:9.8.1.dfsg.P1-4ubuntu0.5 is installed.
         Depends: libisccfg82 (= 1:9.8.1.dfsg.P1-4) but 1:9.8.1.dfsg.P1-4ubuntu0.5 is installed.
         Depends: liblwres80 (= 1:9.8.1.dfsg.P1-4) but 1:9.8.1.dfsg.P1-4ubuntu0.5 is installed.
         Depends: bind9utils (= 1:9.8.1.dfsg.P1-4) but it is not going to be installed.
Internal error: the solver Install(avahi-daemon:i386 0.6.30-5ubuntu2 <libnss-mdns:amd64 0.10-3.2 -> {avahi-daemon:amd64 0.6.30-5ubuntu2 avahi-daemon:i386 0.6.30-5ubuntu2}>) of a supposedly unresolved dependency is already installed in step 21
Internal error: the solver Install(lsb-base:amd64 4.0-0ubuntu20 <avahi-daemon:i386 0.6.30-5ubuntu2 -> {lsb-base:amd64 4.0-0ubuntu20 lsb-base:amd64 4.0-0ubuntu20.2}>) of a supposedly unresolved dependency is already installed in step 37
The following actions will resolve these dependencies:


     Keep the following packages at their current version:
1)     bind9 [Not Installed]                              






Accept this solution? [Y/n/q/?] Y
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.



how should I proceed here?

---

### Post by Kirboosy on 2013-10-09
Take a look at this page from Ask Ubuntu

[How do I Resolve Unmet Dependencies? ]("http://askubuntu.com/questions/140246/how-do-i-resolve-unmet-dependencies")

When you accept that solution what happens afterwords?

Hope that helps!
~Caboose

---

