---
title: "SQL Password"
date: 2007-06-24
forum: Installation &amp; Upgrades
---

### Post by Earltnm on 2007-06-24
Hi, trying to setup My SQL password. It's asking for a password first time in and I don't know what the password is:

iman@iman-desktop:~$ sudo mysqladmin -p -u root -h localhost password newrootsqlpassword
Enter password:
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'


Any ideas?

Thanks, Rick

---

### Post by jack@tortuga on 2007-06-24
Try to do this without using the '-p' option. The default password is blank (rather, it's not set at all). So don't try and login with a password, and you should get in.

---

### Post by spaceW on 2007-06-24
hmm, i have gotten MySQL to work on mine, so maybe i can help.  i think when i first installed it i ran both of these commands one after the other using the same password each time.  i think...

sudo mysqladmin -u root password mysqlpassword
sudo mysqladmin -p -u root -h localhost password mysqlpassword

and, you do realize that the "Enter Password: " line is asking for the root user's password, right?

good luck

---

### Post by Earltnm on 2007-06-25
Thanks for the suggestions, I still must be doing something wrong.  by root password you mean the main password that I use to get into Ubuntu, correct?

When running the two strings you suggest, the first gives me an immediate error (password = no) and the second one gives me this one after I enter my main Ubuntu password:

mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: YES)'
iman@iman-desktop:~$


Any thoughts?  

Thanks!

Rick Morse
Kalamazoo, MI

---

### Post by Earltnm on 2007-06-25
Thanks for the suggestions, I still must be doing something wrong. by root password you mean the main password that I use to get into Ubuntu, correct?

When running the two strings you suggest, the first gives me an immediate error (password = no) and the second one gives me this one after I enter my main Ubuntu password:

mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: YES)'
iman@iman-desktop:~$


Any thoughts?

Thanks!

Rick Morse
Kalamazoo, MI

---

### Post by bclark on 2007-06-25
> **Earltnm said:**
> Thanks for the suggestions, I still must be doing something wrong.  by root password you mean the main password that I use to get into Ubuntu, correct?

When running the two strings you suggest, the first gives me an immediate error (password = no) and the second one gives me this one after I enter my main Ubuntu password:

mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: YES)'
iman@iman-desktop:~$


Any thoughts?  

Thanks!

Rick Morse
Kalamazoo, MI

MySQL has a root user that is completely independent of the ubuntu system, so it will be a different password.  By default it is not set and there are a few ways to set it.  From your error it looks like you don't have a mysql server running locally.

---

### Post by Earltnm on 2007-06-25
Thanks!  That makes a lot of sense. What is best way to get/verify that a local version is working?

---

### Post by bclark on 2007-06-27
> **Earltnm said:**
> Thanks!  That makes a lot of sense. What is best way to get/verify that a local version is working?

you can either try running mysql and see what happens.  or you can run nmap on your system and see if the port is open (default is 3306). or you can run 'ps ax | grep -i mysql'

---

