---
title: "problems with fuse"
date: 2009-03-09
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by hapee on 2009-03-09
I used to work with Quanta using sftp which in Intrepid did not work because of kio slaves: [https://bugs.launchpad.net/ubuntu/+source/kdewebdev/+bug/271074](https://bugs.launchpad.net/ubuntu/+source/kdewebdev/+bug/271074)

So I changed habits and started to use the suggested sshfs without problem:
[https://help.ubuntu.com/community/SSHFS](https://help.ubuntu.com/community/SSHFS)

until I migrated to Jaunty on my test machine and get an error now because:

```
modprobe fuse
FATAL: Module fuse not found.
```

and I tried to rebuild it with the module assistent but that fails too because it can not find the source of fuse.

Any suggestions?

---

### Post by avb on 2009-03-09
probably your issue is not fuse related. fuse is builtin in kernel instead of module now.

---

### Post by hapee on 2009-03-09
thanks for your reply, you are right, if I run sshfs from the prompt it works as it should but if I run sshfsgui it gives an error. I wrote a message to the developer of Sshfsgui and keep working from the prompt for the time being.

---

### Post by pluckypigeon on 2009-03-25
I got the same error...  scary.

Anyway all is well :)

---

