---
title: "User File and Directory access on Edgy"
date: 2007-06-21
forum: Installation &amp; Upgrades
---

### Post by achimwene on 2007-06-21
Hie 

I have installed Kubuntu 6.10 . I then installed samba mainly for file and directory sharing . I have tested , users can logon fine from windows XP machines . However , only the user defined as the owner of a directory can access it , users in the group cannot . Even after defining the group as owning the file also , access is still  not permited . However I then noticed that it has more to do with the OS  than samba as I logged on with CLI as a group user , and cant cd to that directory .

please help

achimwene

---

### Post by vanadium on 2007-06-21
Is the group ownership of the directories properly set? My belief is that the operating system won't allow samba to share directories that do not have the appropriate privileges in the first place.

Execute

ls -l <yourdirectory>

to check the permissions of your directory. If group = root, then that is probably your issue. You would then need to change the group ownership of the directory and subdirectories using a command such as 

chgrp -r <group > <yourdirectory>

---

