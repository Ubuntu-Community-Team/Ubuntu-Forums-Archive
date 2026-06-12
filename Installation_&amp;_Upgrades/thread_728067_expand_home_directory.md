---
title: "expand home directory"
date: 2008-03-18
forum: Installation &amp; Upgrades
---

### Post by kspen on 2008-03-18
Hello everybody
Can you please tell if it is possible to add a new hard disk in my system , but make this hard disk accessible through a specified home directory, Currently i have many data on the disk and it will be a big issue to remove them or anything so i would like if its possible to add the new disk as an addition only to the home directory that i want( and not move the home directory to the new disk).
I hope that i make the question clear enough and i will not confuse anyone
Thank you

---

### Post by prshah on 2008-03-18
> **kspen said:**
> Hello everybody
Can you please tell if it is possible to add a new hard disk in my system , but make this hard disk accessible through a specified home directory, Currently i have many data on the disk and it will be a big issue to remove them or anything so i would like if its possible to add the new disk as an addition only to the home directory that i want( and not move the home directory to the new disk).
I hope that i make the question clear enough and i will not confuse anyone
Thank you

You can add a new harddrive to your system and make it accessible through a specific directory in your /home or any other folder.

For example you can add the new drive, and partition it any way you want; then you can mount it in /home/mine/music or /home/mine/docs or /home/mine/downloads and so on..

```
sudo mkdir ~/downloads
sudo mount /dev/whatever ~/downloads -o auto,users
```

But if you want to MOVE your /home folder to that new drive; that's a whole new kettle of fish, which will involve multiple live CD booting.

(for those who are about to suggest sudo mount --move /home /dev/whatever... sorry that doesn't work.)

---

### Post by ajgreeny on 2008-03-18
However, have a look at [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome) which may be relevant to your wishes to move your home to a separate partition.

---

### Post by kspen on 2008-03-18
cheers guys
i'll try what u say and i hope that it would be ok

---

