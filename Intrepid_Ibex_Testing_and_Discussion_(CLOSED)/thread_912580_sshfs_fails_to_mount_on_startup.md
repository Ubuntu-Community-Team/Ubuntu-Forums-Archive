---
title: "sshfs fails to mount on startup"
date: 2008-09-06
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by tr333 on 2008-09-06
I'm having problems trying to get sshfs to mount on startup when it is defined in fstab.  It mounts correctly if I run "sudo mount -a" after startup has finished.  I was going to file a bug on launchpad, but i'm not sure what package to file this against.

---

### Post by taavikko on 2008-09-07
What is your fstab like?

it has to go something like this

sshfs#my-remote-user@my-remote-host:/home/my-remote-user /my-local-filesystem/remotefs fuse defaults 0 0

---

### Post by tr333 on 2008-09-07
```
sshfs#share@192.168.0.7:/home/share/music /mythtv/music fuse uid=1000,gid=1000,allow_other 0 0
```

---

