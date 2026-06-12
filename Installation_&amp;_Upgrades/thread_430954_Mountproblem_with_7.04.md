---
title: "Mountproblem with 7.04"
date: 2007-05-02
forum: Installation &amp; Upgrades
---

### Post by medde on 2007-05-02
I've upgraded my Ubuntu from 6.10 to 7.04 and everything went just fine. Except for that I had an automatic mounted smb-disk on my Desktop. The server runs Ubuntu 6.06 server and the fstab line that worked fine with 6.06 looks like this: "//192.168.1.3/public /home/per/Desktop/Kerberos smbfs username=per,password=XXX,uid=per,gid=users,iocharset=utf8,codepa
ge=unicode,unicode 0 0" It doesn't work on 7.04. Anyone who has a clue or maybe can tell me how to "see" if there is some kind of error message from the mount attempt in fstab.

---

### Post by medde on 2007-05-02
Sorry, sorry. I solved this one my self. The problem was that the mountline in fstab lacked an end of line char at the end. How would one know?

---

