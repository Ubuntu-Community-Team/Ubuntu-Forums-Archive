---
title: "Username problems"
date: 2008-06-24
forum: Installation &amp; Upgrades
---

### Post by solracsuii on 2008-06-24
I installed Ubuntu Studio this evening, and i can't access the system because of some error in the username while accesing the system:
[B]
-bash: /dev/null: Permission denied
[/B]
any ideas m8s?

thanks

---

### Post by iaculallad on 2008-06-24
That's a permission problem with your /dev/null. Try to see the permission by issuing the **ls** command on your terminal:

```
ls -l /dev/null
```

and should equal to:

> crw-rw-rw- 1 root root 1, 3

If you got a different permission, RM your /dev/null and try to recreate it as root (**sudo -i**, and input your own password).

```
sudo -i
rm /dev/null
mknod -m 0666 /dev/null c 1 3
```

---

### Post by tamoneya on 2008-06-24
what exactly are you trying to do at the moment.  If you are attempting something in command line just precede it with sudo to gain root permissions.

---

### Post by solracsuii on 2008-06-24
ok, im really new to linux, so i need u to help me step by step, the terminal will be?

---

### Post by iaculallad on 2008-06-24
> **solracsuii said:**
> ok, im really new to linux, so i need u to help me step by step, the terminal will be?

Navigate to Applications->Accessories->Terminal and follow the steps i posted above.

---

### Post by solracsuii on 2008-06-24
i can't get it the system, this all happens on DOS, when u start the pc black screen lol...:confused:

---

### Post by iaculallad on 2008-06-24
> **solracsuii said:**
> i can't get it the system, this all happens on DOS, when u start the pc black screen lol...:confused:

Try to login using the Restore mode.

---

### Post by solracsuii on 2008-06-24
same thing there :(

could it be the istallation failed? 
i installed in a Partition i made in one of my hardisks.
how can i intall again because it made the linux partition swap etc already

---

### Post by Bubba64 on 2008-06-24
If you have internet access on another computer this helped me with the very same problem.
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
Actually I neglected to notice that your trying to get Ubuntu studio working my problem was getting the login to work on Gutsy.

---

### Post by solracsuii on 2008-06-25
ok, i did what u asked, still doesnt work.

same message:
-bash: /dev/null: Permission denied

it seems when it's loading everything something wrong with the

hardware drives appears infront : Failed

i think it's not the password at all.

---

