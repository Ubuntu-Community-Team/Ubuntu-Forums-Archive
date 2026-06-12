---
title: "su password?"
date: 2010-12-14
forum: Installation &amp; Upgrades
---

### Post by siva_chowdhary on 2010-12-14
guys how can i change my su password i dont know what i did n im not able access as super user soo plz help me guys how can i change my su password i dont know the previous passowrd waiting for your reply thanks in advance

---

### Post by ajgreeny on 2010-12-14
Ubuntu does not use the same manner of gaining root access as most linux distros, so have a look at [Ubuntu: RootSudo]("https://help.ubuntu.com/community/RootSudo") which will tell you all about it.

---

### Post by surfer on 2010-12-14
if you are in the admin group, you can use su to gain root access. the password is your **user password** then.

---

### Post by ajgreeny on 2010-12-14
> **surfer said:**
> if you are in the admin group, you can use su to gain root access. the password is your **user password** then.
No ,you can't!  Not quite.

Try **su** in terminal and you'll see what I mean.

You can use **sudo su**, if you really must, but there is often little need for that as **sudo <command>** will do the same thing.

sudo su could be useful if carrying out a complex sequence of commands that take a long time, and where the default timeout of the sudo root permissions might occur, but if you're doing that kind of complex terminal work, you would probably know enough to get a proper root account enabled.  For most users sudo command is sufficient.

See Root-Sudo in my signature.

---

### Post by kukker32 on 2010-12-14
I don't know how to recover a lost password if it's that thats the problem..

but try set a new.. doing the following


[LIST=1]
[*][FONT=Verdana][SIZE=2]Click **Applicatons** -> **Accessories**. Click **Terminal**.[/SIZE][/FONT]
[*][FONT=Verdana][SIZE=2]A new window appears with a prompt.  Key in “[/SIZE][/FONT][FONT=Verdana][SIZE=2]**sudo passwd**“.[/SIZE][/FONT]
[*][FONT=Verdana][SIZE=2]System will prompt you to enter the new root password twice.  Now, you are done with your new root password.[/SIZE][/FONT]
[/LIST]

should be helping, let me know if it dosn't

---

### Post by Rubi1200 on 2010-12-14
You can also reset the password using this tutorial:
[http://psychocats.net/ubuntu/resetpassword](http://psychocats.net/ubuntu/resetpassword)

---

### Post by surfer on 2010-12-14
> **ajgreeny said:**
> No ,you can't!  Not quite.

Try **su** in terminal and you'll see what I mean.

You can use **sudo su**, if you really must, but there is often little need for that as **sudo <command>** will do the same thing.

sudo su could be useful if carrying out a complex sequence of commands that take a long time, and where the default timeout of the sudo root permissions might occur, but if you're doing that kind of complex terminal work, you would probably know enough to get a proper root account enabled.  For most users sudo command is sufficient.

See Root-Sudo in my signature.

ups, i meant **sudo**, of course... thanks for correcting me.

---

### Post by sohail_linux on 2010-12-14
jus type in terminal
 
sudo su
 
then enter ur account password. Now you are in root account. You can change root password by
 
passwd

---

### Post by tkzv on 2010-12-14
> **ajgreeny said:**
> 
You can use **sudo su**, if you really must, but there is often little need for that as **sudo <command>** will do the same thing.

By the way, what is the difference between **sudo su** and **sudo sh** in Ubuntu?

---

### Post by surfer on 2010-12-14
> **tkzv said:**
> By the way, what is the difference between **sudo su** and **sudo sh** in Ubuntu?

i do not know that... i prefer:
```
$ sudo -i
```
or
```
$ sudo -s
```

---

