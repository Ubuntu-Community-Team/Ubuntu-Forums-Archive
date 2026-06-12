---
title: "no matter  what i try  cannot change nor acces mysql server"
date: 2007-11-25
forum: Installation &amp; Upgrades
---

### Post by firedancer on 2007-11-25
i tried all the explanation around , google, ubuntu docs, 

followed , but i installed and purged mysql about 5 times , everytime it removes amarok and i have to install that back , 

i'm trying to set up a lamp , but mysql gives me

```
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
law@sTToned:~$ mysql
ERROR 1045 (28000): Access denied for user 'law'@'localhost' (using password: NO)
law@sTToned:~$ sudo apt-get --purge remove mysql-server mysql-common mysql-client
 
``` 


i'll just remove it again and install amarok rite after , 

hajajai, 

firedancer

i have a fresh kubuntu gutsy install ,what can be the problem

---

### Post by firedancer on 2007-11-26
and now my whole system seems unstabe 

can't add a user or make any changes , 

on my other pc kubuntu is doing alrite

and i just put up apache with php good to start cause my debian server is kaput 

and what now , 

i think i'll just go with server-install , needed the gui because of noobyness

just want to start making some dynamic webpages , it's been a month , and all i got is static pages and failing to do some real programming:confused:  

want to start , but it's against me :(

---

### Post by Linteg on 2007-11-26
Well, for starters, you need to log in with a password, which you have to set when you install the mysql-server package. Mysql is a bit dumb in this regard, it doesn't ask for password unless you start it with
```
mysql -p
#so to start it as the root user you have to run:
mysql -u root -p
```
and you will be prompted for the password.

---

### Post by firedancer on 2007-11-30
tried that already t believe, 

uninstalled the whole thing , checking out another option

thnx anyway, well or maybe i skipped that , cause on my debian server , i had no such problems, well i'll make sure next time

---

