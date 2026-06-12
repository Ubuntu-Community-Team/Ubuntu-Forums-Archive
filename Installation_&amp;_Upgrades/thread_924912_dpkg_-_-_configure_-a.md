---
title: "dpkg - - configure -a"
date: 2008-09-20
forum: Installation &amp; Upgrades
---

### Post by F8M on 2008-09-20
How do I manually run 'dpkg --configure -a' to correct the problem in drive E of my Vista/Ubuntu 8.04.1 dual boot.
Can somebody help me.

---

### Post by jolx on 2008-09-20
open a terminal and type:
```
sudo dpkg --configure -a
```

---

### Post by iaculallad on 2008-09-20
> **F8M said:**
> How do I manually run 'dpkg --configure -a' to correct the problem in drive E of my Vista/Ubuntu 8.04.1 dual boot.
Can somebody help me.

You need an administrative privilege to execute that command, to achieve this, you need to insert the command 'sudo' which means you are to execute that command as another user.

```
sudo dpkg --configure -a
```

Input your own user password, and don't worry if you don't see the characters you input as not being echoed back on the screen, that's just a security feature for the terminal. Input your password and press the Enter key.

---

### Post by F8M on 2008-09-20
> **iaculallad said:**
> You need an administrative privilege to execute that command, to achieve this, you need to insert the command 'sudo' which means you are to execute that command as another user.

```
sudo dpkg --configure -a
```

Input your own user password, and don't worry if you don't see the characters you input as not being echoed back on the screen, that's just a security feature for the terminal. Input your password and press the Enter key.
After putting the command you requested, I received this message
"dpkg: parse error, in file '/var/lib/dpkg/update/0006' near line 1: newline in field name 'more.'"
Can you help me, this is way above me. Thanks

---

### Post by iaculallad on 2008-09-20
> **F8M said:**
> After putting the command you requested, I received this message
"dpkg: parse error, in file '/var/lib/dpkg/update/0006' near line 1: newline in field name 'more.'"
Can you help me, this is way above me. Thanks

Try removing the file(s) in the /var/lib/dpkg/updates folder:

```
sudo rm /var/lib/dpkg/updates/*
```

Then:

```
sudo dpkg --configure -a
```

---

### Post by F8M on 2008-09-20
> **iaculallad said:**
> Try removing the file(s) in the /var/lib/dpkg/updates folder:

```
sudo rm /var/lib/dpkg/updates/*
```

Then:

```
sudo dpkg --configure -a
```


I think it worked, the following is the result:
"Setting up apache2-utils (2.2.8-lubuntu0.3) ...
 Setting up apache2.2-common (2.2.8lubuntu0.3) ...
 Setting up apache2-mpm-prefork (2.2.8-lubuntu0.3) ...
  * Starting web server apache2
 apache2: Could not reliably determine the server's fully qualified domain name.
 using 127.0.1.1 for ServerName
 http (pid 5608) already running                      [OK]
 Setting up libapache2-mod-php5 (5.2.4-2ubuntu5.3) ..."
Now let's see if I can get my wireless to work. 
A BIG THANK YOU. And by the way, you have a cute son, whereas I have 8kids.

---

