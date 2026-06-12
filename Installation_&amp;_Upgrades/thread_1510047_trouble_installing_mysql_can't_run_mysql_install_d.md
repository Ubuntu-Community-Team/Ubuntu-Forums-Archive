---
title: "trouble installing mysql can't run mysql_install_db"
date: 2010-06-15
forum: Installation &amp; Upgrades
---

### Post by cactusfrog on 2010-06-15
OS: Ubuntu 10.04 LTS

i am having trouble getting a mysql database working. 
I following instructions from a book titled*Build your own Database Driven Web Site*. I copied everything perfectly from the book yet the final step doesn't work. 
this is after a clean install of Ubuntu 10.04 LTS
```
dexter@ubuntu:~$ sudo su
[sudo] password for dexter: 
root@ubuntu:/home/dexter# cd /usr/local
root@ubuntu:/usr/local# tar xfz ~dexter/Desktop/mysql-5.1.47-linux-i686-glibc23.tar.gz
root@ubuntu:/usr/local# ls 
bin  etc  games  include  lib  man  mysql-5.1.47-linux-i686-glibc23  sbin  share  src
root@ubuntu:/usr/local# ln -s mysql-5.1.47-linux-i686-glibc23 mysql
root@ubuntu:/usr/local# cd mysql
root@ubuntu:/usr/local/mysql# groupadd mysql
root@ubuntu:/usr/local/mysql# useradd -g mysql mysql
root@ubuntu:/usr/local/mysql# chown -R mysql .
root@ubuntu:/usr/local/mysql# chgrp -R mysql .
```
```


[COLOR="Red"]**root@ubuntu:/usr/local/mysql# scripts/mysql_install_db --user=mysql**
scripts/mysql_install_db: 244: ./bin/my_print_defaults: not found
Neither host 'ubuntu' nor 'localhost' could be looked up with
./bin/resolveip
Please configure the 'hostname' command to return a correct
hostname.
If you want to solve this at a later stage, restart this script
with the --force option
[/COLOR]
```
I also tried 
```
root@ubuntu:/usr/local/mysql# scripts/mysql_install_db --dexter=mysql
scripts/mysql_install_db: 244: ./bin/my_print_defaults: not found
Neither host 'ubuntu' nor 'localhost' could be looked up with
./bin/resolveip
Please configure the 'hostname' command to return a correct
hostname.
If you want to solve this at a later stage, restart this script
with the --force option
```
i don't see anything wrong with this statement nor can i figure out what it means. I thought it might be complaining about the file not existing but i checked and the file is in the location /usr/local/mysql/scripts

---

### Post by lechien73 on 2010-06-15
Are you using the 64-bit or 32-bit edition of Lucid?

The "my_print_defaults" and hostname errors could indicate that you're using a 32-bit tarball on 64-bit architecture.

You could also try the following from the mysql directory:

```
./bin/resolveip `hostname`

```
and compare this output with the contents of your /etc/hosts file.

---

### Post by cactusfrog on 2010-06-15
i didn't try to install 64bit ubuntu but that would explain why i was having trouble getting flash player working with the error amd64. I don't really know how i would have ****ed up something so simple as installing the proper bit os but who knows. Is there any command that will tell me if i am running 64 or 32 bit?

---

### Post by lechien73 on 2010-06-15
Yes...open a terminal window and type:

```
uname -a
```

If you see "x86_64", then you're running Lucid 64bit.

---

### Post by cactusfrog on 2010-06-16
apparently i installed the wrong os somehow so i installed the same version just 32 bit but i still get the same error 
> root@ubuntu:/usr/local/mysql# scripts/mysql_install_db --dexter=mysql
scripts/mysql_install_db: 244: ./bin/my_print_defaults: not found
Neither host 'ubuntu' nor 'localhost' could be looked up with
./bin/resolveip
Please configure the 'hostname' command to return a correct
hostname.
If you want to solve this at a later stage, restart this script
with the --force option
root@ubuntu:/usr/local/mysql# 


---

