---
title: "Kernel upgrade"
date: 2010-09-09
forum: Installation &amp; Upgrades
---

### Post by chaeu1986@gmail.com on 2010-09-09
[FONT=Comic Sans MS][SIZE=3]i am using Ubunntu 10.04, kernel version 2.6.32-24 generic. However, i am getting constant update for the same kernel version. thought it might be an error, i did an update.  however it is still showing like that.

I recently cleared my previous kernel versions ie 21, 22. i do have the version 23 as a back up but i use the version 24. kindly suggest what to do. 


[/SIZE][/FONT]

---

### Post by mohansathish on 2010-09-09
Is that a Kernel upgrade or update of other packages?

Are you listed with same updates all the time? Each products like firefox, pidgin, GIMP and all applications check for updates and they do them with trusted repositories. If you have the same files updated repeatedly, report to this thread.

---

### Post by slakkie on 2010-09-09
Could you plpease show us the output of:

```

dpkg -l | egrep "linux-(image|headers)"

```

Show us the output of that command.

Then look for something that says:

```

linux-image-generic
linux-headers-generic 

```

generic could be ec2, pae, rt, server or virtual. 

Then do:
```

apt-cache policy linux-image-generic linux-headers-generic 

```

And show us this output too. Thanks!

---

