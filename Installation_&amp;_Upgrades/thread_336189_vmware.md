---
title: "vmware"
date: 2007-01-11
forum: Installation &amp; Upgrades
---

### Post by kuliand on 2007-01-11
i have installed vmware server but when i enter vmware into the terminal i get the following error message,

andrew@andrew-desktop:~$ vmware
exec: 180: /usr/lib/vmware-player/lib/wrapper-gtk24.sh: not found

any ideas on how to resolve this?

---

### Post by computergroove on 2007-01-11
andrew@andrew-desktop:~$ vmware
exec: 180: /usr/lib/vmware-player/lib/wrapper-gtk24.sh: not found

I would look to see if the file wrapper-gtk24.sh exists in the specified location. If not I would so a search for the file and put it in that directory and see if it loaded. Where ever you find the file (assuming that you do) you might want to put all the files in that location into the location that your error message tells you they need to be. If you cant find the file than you have installed it wrong.

---

