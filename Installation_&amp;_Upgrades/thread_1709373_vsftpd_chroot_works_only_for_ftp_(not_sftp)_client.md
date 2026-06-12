---
title: "vsftpd chroot works only for ftp (not sftp) clients"
date: 2011-03-18
forum: Installation &amp; Upgrades
---

### Post by dag1 on 2011-03-18
I have a partion called /media/Project

I have users under /home:  /home/user1   /home/user2 ...

I want their homes to be under the above partition so 
I moved their home folders to /media/Project
and create a symbolic link 

so /home now has:

user1  -> /media/Project/user1
user2  -> /media/Project/user2

..


I set up vsftpd.conf to have:

chroot_local_user=YES

I use FileZilla client to login as user1. First in mode of "ftp". I log in and indeed see chroot working (I see / as the home directory).

But when I change into mode "sftp" in FileZilla and relogin (as the same user) now I am able to traverse up the real tree since I see 

/media/Project/user1

and I can enter /media/Project

or any other folder under /media

and in fact under /


My question: How can I ensure that even if the user is using  sftp then he will not be able to go outside his home ?

thanks

Dag

---

