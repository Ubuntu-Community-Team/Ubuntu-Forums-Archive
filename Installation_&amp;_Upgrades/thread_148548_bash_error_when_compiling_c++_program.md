---
title: "bash error when compiling c++ program"
date: 2006-03-22
forum: Installation &amp; Upgrades
---

### Post by orangecat on 2006-03-22
i get a bash error when i try compiling the c++ program
the error says:
bash: c++: command not found
or when i try to compile using g++, it gives the same error
how can this be corrected?

---

### Post by IYY on 2006-03-22
sudo apt-get install g++

---

### Post by orangecat on 2006-03-22
thanks for ur reply...
i tried doin tht but i get some more error msgs abt backports..like..

W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)

wht do i do now?

---

### Post by NetMatrix on 2006-03-22
Check in the GUI to see if all your repositories are not hidden and you have them checked as available.

System / Administration / Synaptec Package Manager

     in program: settings / repositories

     in new window click Settings

     in new window make sure Show disabled software sources is checked : close window

     in previous window check all available software sources.  Close all windows and the package management program then run

sudo apt-get install g++

Should work.  Good luck.

---

### Post by orangecat on 2006-03-22
i installed the g++ thing frm the synaptic manager..thanks anyway,,

wht i wanna knw now is..wht do i do abt these backports errors?
ive tried wht netmatrix said in the synaptic manager..but after i try to apply the changes it gives still more error msgs of the same type 

[http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/Packages.gz:](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/Packages.gz:) 404 Not Found
[http://ubuntu-backports.mirrormax.net/dists/hoary-backports/universe/binary-i386/Packages.gz:](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/universe/binary-i386/Packages.gz:) 404 Not Found
[http://ubuntu-backports.mirrormax.net/dists/hoary-backports/multiverse/binary-i386/Packages.gz:](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/multiverse/binary-i386/Packages.gz:) 404 Not Found
[http://ubuntu-backports.mirrormax.net/dists/hoary-backports/restricted/binary-i386/Packages.gz:](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/restricted/binary-i386/Packages.gz:) 404 Not Found

wht now?

---

