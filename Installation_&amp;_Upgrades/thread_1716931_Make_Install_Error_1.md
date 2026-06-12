---
title: "Make Install Error 1"
date: 2011-03-29
forum: Installation &amp; Upgrades
---

### Post by MrMeier on 2011-03-29
Hey.

I'm making a cluster with some old computers, and I'm following this guide: [http://www.linux.com/community/blogs/Building-a-Beowulf-Cluster-in-just-13-steps-.html](http://www.linux.com/community/blogs/Building-a-Beowulf-Cluster-in-just-13-steps-.html)

I'm at step 9, and it's going fine, until the command "Make Install".
It just say 

"if [ "/home/mpiuser/Desktop/mpich1" = "/home/mpiuser/Desktop/mpich1" ] ; then \
        ./bin/mpiinstall  ; \
    else \
        ./bin/mpiinstall -prefix=/home/mpiuser/Desktop/mpich1  ; \
    fi
cp: `/home/mpiuser/Desktop/mpich1/bin/tarch' and `/home/mpiuser/Desktop/mpich1/bin/tarch' are the same file
**Error copying file /home/mpiuser/Desktop/mpich1/bin/tarch to /home/mpiuser/Desktop/mpich1/bin/tarch **
make: *** [install] Error 1"

I have tried with Sudo Make Install, but that didn't work either, and that's what all write on google..
So please help me, and say if you need more info :)

---

