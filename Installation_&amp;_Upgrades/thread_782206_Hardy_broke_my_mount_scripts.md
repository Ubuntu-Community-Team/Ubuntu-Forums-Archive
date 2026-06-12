---
title: "Hardy broke my mount scripts"
date: 2008-05-04
forum: Installation &amp; Upgrades
---

### Post by advoss on 2008-05-04
There appears to be a change in either samba support or mount in the version that was inclueded in hardy, i have scripts like the following that i would run to mount what i wanted from my server.

```

##/bin/bash

sudo mount -t smbfs -o username=me,password=******,uid=me,gid=me //file/multimedia /mnt/samba/multimedia
```

since I upgraded i get this error message when i launch one of them:
mount error: could not find target server. TCP name file/storage not found
No ip address specified and hostname not found

However my server is running fine and I can access the files using smb:  in dolphin.  What do I need to do to fix my scripts?

Thanks in advance!

---

### Post by advoss on 2008-05-04
This guide fixed it: [http://ubuntuforums.org/showthread.php?t=88206&highlight=netbios](http://ubuntuforums.org/showthread.php?t=88206&highlight=netbios)

Though I didn't need to do thoes things before upgraded and would like to know what changed that made it nessicary to have another daemon running now.

---

