---
title: "AptMoveHowto errors?"
date: 2006-05-29
forum: Installation &amp; Upgrades
---

### Post by rduch on 2006-05-29
I am trying to follow the AptMoveHowto to update a computer that is not internet connected. The terminal output so far is as follows:

rene@ubuntu:~$ sudo apt-get autoclean
Reading package lists... Done
Building dependency tree... Done
Del mysql-common 4.0.24-10ubuntu2.2 [34.9kB]
Del mysql-common 4.0.24-10ubuntu2.1 [34.7kB]
Del libmysqlclient12 4.0.24-10ubuntu2.1 [292kB]
Del libmysqlclient14 4.1.12-1ubuntu3.2 [1474kB]
Del libmysqlclient12 4.0.24-10ubuntu2.2 [292kB]
Del libmysqlclient14 4.1.12-1ubuntu3.3 [1475kB]
rene@ubuntu:~$ mount /media/cdrom0
rene@ubuntu:~$ for f in 'find /media/cdrom/pool/ -name '*.deb' -printf %f\\n' do if [ -f /var/cache/apt/archives/$f ]; then sudo rm -v /var/cache/apt/archives/$f fi done
bash: syntax error near unexpected token `then'
rene@ubuntu:~$ 

1. What scripting language may have been used here? I am not familiar with it so I am unsure what the syntax error may be. 
2. Is the 'fi' just before 'done' correct or should it be 'if' ?
3. Further into the Howto the is a line stating that "we need to make Relaease.gpg, to make it you must already have your GPGKey set and ready to sign. Is that done further down with the line "gpg --export -a "Your Name" > public.key" ? What is GPG
4. The next line says "change "Your Name" with the name that you use in your PGP. Is the "PGP a typo? Where is this GPG or PGP and how do I know what name is used for it?

Many thanks in advance

Rene

---

### Post by az on 2006-05-29
It's in bash and the fi is the end of an if.


Try 
wiki.ubuntu.com/AptMoveHowto/simple

You don't need to sign your archive if your not distributing it, right?

---

### Post by rduch on 2006-05-29
Thanks for the quick reply.

The AptMoveHowto/simple did not show up on my search for some reason. I will try that next. I'll post the results soon and I'll look into bash scripts when I have time to see if I can get a little more familiar with it.

BTW my family is from the trois riveres area about three or four generations ago. One of these fine days I'll look into that history and see what surprises are is store for me. 

Thanks again,

Rene

---

### Post by rduch on 2006-05-29
Excellent! Everything worked as advertised.

Blessings to one and all,

Rene

---

