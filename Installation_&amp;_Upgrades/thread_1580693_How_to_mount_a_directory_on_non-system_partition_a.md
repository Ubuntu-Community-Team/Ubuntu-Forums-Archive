---
title: "How to mount a directory on non-system partition as /home?"
date: 2010-09-23
forum: Installation &amp; Upgrades
---

### Post by irjozagata on 2010-09-23
... fstab can hold only block device (partition) to be mounted as home, not a directory(?)
Manual
  mount --bind /media/raid-data/users /home  ...
works es expected, but I don't know how to "bind" directory to /home via fstab to be properly mounted during boot.
(/media/raid-data is the mount point of my /dev/md2 partition, which is raid1 data volume I want have my /home there.)

Do  I need to start nfs server to be able to mount the /users directory  from localhost in fstab or there is another way? This way I probably  need to export my /users directory for localhost (/etc/exports) nad  further edit /etc/auto.master and /etc/auto.direct ?

All of posts I could find so far say to mount entire (root of) separate partition as home (e.g.  fstab says: /dev/md0    /home ..... 0, 0), while I would like to have  my users' directories 1 level down - let say in /users directory of my  data partition.

Being Ubuntu-positive for few weeks only, any advice is welcome - thanks in advance
Not needed to describe me detail on how to copy data etc. - tell me just principle how to do it.
Irjo

---

### Post by Lateralis on 2010-09-23
To be honest, I have no clue about most of the questions you raise in your post.  What I do know how to do is bind files in fstab!

```

/media/raid-data/users   /home   none   bind   0    0

```

Of course, this just mirrors your above command - you can change the first and second directories to point to the data and the target.  

Also, just a note actually... fstab cannot contain quotes, spaces or most other special characters.  You will need to replace such characters with their correct character code.  The hypen though is OK.

---

### Post by irjozagata on 2010-09-23
Thanks, Lateralis - /home dir binding has been solved with your advice.
I overlooked in man fstab: "... An entry  none  is  useful for bind or move mounts. ..."
However, this is the only (and indirect) mention about possibility to bind dir instead of mounting entire partition - not that clear for Linux novice like me.
regards
Irjo

---

