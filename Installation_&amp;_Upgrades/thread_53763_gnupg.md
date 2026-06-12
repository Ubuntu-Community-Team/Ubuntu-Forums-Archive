---
title: "gnupg"
date: 2005-08-02
forum: Installation &amp; Upgrades
---

### Post by lightseeker on 2005-08-02
Hi

i am tring to configure enigmail. I installed both enigmail and the gnupg from the
symantic package manager. i required the  keys needed  but when i 
try to send an encypted email it popped up this error msg

Error - encyption command failed

/usr/bin/gpg -charset utf8 --batch --no-tty --status-fd 2 --with -finderprint - fixed-list-mode--with- colons --list-keys

gpg:error creating keyring `/home/johnny/.gnupg/pubring.gpg':Permission denied
gpg:/home/kerm/.gnupg/trustdb.gpg :can't access : Permission denied
gpg: fatal : can't init trustdb: trust database error
secmem usage : 0/0 bytes in 0/0 blocks of pool 0/32768

helpppp!!

---

### Post by dabeej on 2005-08-02
check the permissions on .gnupg

ls -l ~/.gnupg
if there isn't one
mkdir ~/.gnupg

---

### Post by lightseeker on 2005-08-02
the file exist but  i can't access it.  
i try 

johnny@compy:~$ ls -l ~/.gnupg
ls: /home/johnny/.gnupg: Permission denied

how do i change the permission?

---

### Post by kosmic on 2005-08-02
with the Chmod comand do a man chmod.

our 

Sudo chmod 777 filename you want, but attention 777 will give Read/Write/Execute acess to anyone including you (The user) the Group and Anyone else in the world :)

---

