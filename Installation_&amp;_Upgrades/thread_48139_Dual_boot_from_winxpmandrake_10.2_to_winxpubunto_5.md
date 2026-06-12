---
title: "Dual boot from winxp/mandrake 10.2 to winxp/ubunto 5.04"
date: 2005-07-11
forum: Installation &amp; Upgrades
---

### Post by firestarter on 2005-07-11
hi guys... 

i have a problem. i currently have a winxp/mandrake 10.2 setup at home. i wanna change to mandrake to ubuntu without changing the current partition setup. BUT, i seem to have hit a wall somewhere. when asked for the partitions, it can't seem to detect my current partition setup, and it seems like i have to repartion the entire hard drive. mind you guys, i don't really wanna reinstall everything (i have a sister who shares my pc, so she has her own settings already, out of respect). i also had this same prob with fedora. further info: i partitioned this first using winxp. i installed ubuntu 4.?? (the one before this) then i installed mandrake 10.1, upgraded to 10.2 all with no probs. 

i really appreciate your help on this. THANKS!  :)

---

### Post by Xian on 2005-07-11
Well, Ubuntu uses parted for its partitioning, so perhaps there is a problem with your disk that is causing parted to fail, and therefore only give you the entire drive option during installation. When you are in mandrake (make sure you have parted installed), open a terminal and issue the command listed below. You should get a similar output with no error messages. When finished type 'quit' to exit the program.

```
 $su
# parted
GNU Parted 1.6.20 with HFS shrink patch 16
Copyright (C) 1998 - 2004 Free Software Foundation, Inc.
This program is free software, covered by the GNU General Public License.

This program is distributed in the hope that it will be useful, but WITHOUT ANY
WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A
PARTICULAR PURPOSE.  See the GNU General Public License for more details.

Using /dev/hda
(parted) 
```

---

