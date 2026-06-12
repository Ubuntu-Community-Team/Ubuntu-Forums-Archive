---
title: "problems with  installation of  mysql (5)"
date: 2006-10-20
forum: Installation &amp; Upgrades
---

### Post by balki2005 on 2006-10-20
Hello everybody,

I try  to  follow  the  procedure to  install   mysql from   Unofficial Ubuntu 6.06 (Dapper Drake) Starter Guide.

And when  I try to  execute  this  part [I]"

    * MySQL comes with no root password as default. This is a huge security risk. You'll need to set one. So that the local computer gets root access as well, you'll need to set a password for that too. The local-machine-name is the name of the computer you're working on. For more information see here 

mysqladmin -u root password your-new-password
mysqladmin -h root@local-machine-name -u root -p password your-new-password
sudo /etc/init.d/mysql restart"[/I]

**then  I recieve this  error:**

jonay@thunderbird:~$ mysqladmin -h root@thunderbird -u root -p password luna2005Enter password:
mysqladmin: connect to server at 'root@thunderbird' failed
error: 'Unknown MySQL server host 'root@thunderbird' (1)'
Check that mysqld is running on root@thunderbird and that the port is 3306.
You can check this by doing 'telnet root@thunderbird 3306'
jonay@thunderbird:~$

who  can help  me  ?

thanks in advance,

Balki2005

---

### Post by Arby on 2006-10-20
Have you tried that telnet command it recommends to see if mysql is actually running? If you don't understand the output post it here.

Another way of checking mysql is running is like this
```
ps -e | grep mysql
``` If you see something like this
```
processID  something Time Name
4599 ?      00:00:00 mysqld_safe
4637 ?      00:46:49 mysqld
```then mysql is running (processID and time will be different for your system). You won't see the headers, that's just so you know what they are

Let us know what the outcome of that is.

Edit: if mysql is not running try ```
sudo /etc/init.d/mysql start
```
Sorry I should have put that in the original post.

---

### Post by balki2005 on 2006-10-21
hello,

thanks  for  the reply ! here  is  the  outcome:

jonay@thunderbird:~$ ps -e | grep mysql
 4686 ?        00:00:00 mysqld_safe
 4750 ?        00:00:00 mysqld
jonay@thunderbird:~$

I can  work  with  mysql, but  why  recieve  that  error message  ? do  I something wrong  ?

thanks  in advance,

Balki2005

---

### Post by Arby on 2006-10-21
OK well your mysql server is running then so that rules that out. Just re-reading your original post that mysqladmin command looks a little odd, try it like this
```
mysqladmin -h thunderbird -u root -p password your-new-password
``` i.e. drop the 'root@' from the hostname. If that doesn't work try this one
```
mysqladmin -h localhost -u root -p password your-new-password
```

---

