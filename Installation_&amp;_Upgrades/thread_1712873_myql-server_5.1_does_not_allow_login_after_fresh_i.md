---
title: "myql-server 5.1 does not allow login after fresh install"
date: 2011-03-23
forum: Installation &amp; Upgrades
---

### Post by gruadp on 2011-03-23
I just installed 10.04 LTS and installed mysql-server 5.1. During install I had to enter a password and verify it. Standard procedure.

But now I cannot login.

root@mycomputer:~#mysql -u root -p
Enter password:
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)

mysql is running and nothing in mysql-logs. I rebooted the machine and reinstalled mysql-server several times using the following commands:

apt-get remove --purge mysql-server mysql-server-5.1 mysql-server-core-5.1 mysql-common

and

apt-get install mysql-server mysql-server-5.1 mysql-server-core-5.1 mysql-common

I tried a different password or an empty password on my reinstall-attempts, but nothing changed.  I couldnt find a way to access mysql. 

any ideas? anyone with a similar problem?

thnx,
p

---

### Post by gruadp on 2011-03-23
solved.  

I did two things and I dont know which solved my problem:

1)
I did a apt-get update  which probably brought me a new version of mysql-server 5.1 on the next install.  If this solved my problem it would mean that there is a broken package out there. (I doubt it cause I would have found more people with a similar problem on my google-research, but one never knows what special things goes on my computer - especially as I run ubuntu-64)

2)
After another try to purge all packages I searched my system for remaining files named *mysql* and found a few files.  I manually deleted this files and directories and then installed mysql-server again and now everything works as expected.

so my personal theory is that I made a double-typo when first installing mysql (entering the wrong password two times due to typing to fast) and when purging the package the old password stayed somewhere and was not overwritten on the reinstall.  yeah - doesnt sound like a very good theory, but at last my mysql-server finally works

p

---

