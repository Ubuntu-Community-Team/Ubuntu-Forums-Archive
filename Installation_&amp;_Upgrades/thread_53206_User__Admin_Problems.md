---
title: "User  Admin Problems"
date: 2005-07-30
forum: Installation &amp; Upgrades
---

### Post by byteco on 2005-07-30
I'VE INSTALLEd UNBUNTU 5.O4 IN MY LAPTOP AND i CANNOT DO ABY adminitrative operations with my user. I put my passwor for exan«mple n user-admin and it does not work

ErroSr: Failed to run users-admin:
 Child terminated with 194 status

OR Failed to run users-admin:
 Child terminated with 1 status

I've managed some things in su root and sudo but Why do I ha ve always error and I cannot use the interfaces?

Terminal errors: 

root@XXXX:/home/XXXX # sudo users-admin

(users-admin:9904): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.


Note: I'm a novice...so please reply with some detail..

Byteco

[www.byteco.pt](www.byteco.pt)

 ](*,)  ](*,)

---

### Post by kosmic on 2005-07-30
are you trying to sudo with a root account ?

 root@XXXX:/home/XXXX # sudo users-admin


Did you do a normal instalation or expert instalation ?

what the content of your sudo file, cat /etc/sudoers ?

---

