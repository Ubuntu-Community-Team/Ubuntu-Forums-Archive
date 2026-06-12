---
title: "Cannot change user in 18.04"
date: 2018-04-26
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2018-04-26
I had to reinstall 18.04 earlier today.  I made the mistake of calling myself john instead of johnl .So, I set up another user called johnl.  However, 18.04 will not let me log into johnl.  Reason for change is that my evolution files are under johnl.

How do I get to log myself in as johnl.  I am the only user of my PC.

John

---

### Post by sevendogsbsd on 2018-04-26
Does your new (incorrect) user "john" have sudo access? If so, use sudo to set johnl's password so you can get in the account. Example:

```
 sudo passwd johnl
```

---

### Post by cigtoxdoc on 2018-04-26
Thank you very much for your reply.  Yes, I could reset the password and login into johnl with the reset password.  However, the desktop never comes up and it asks for my password again.  In the distant past, this was due to lack of the right desktop program.  John

---

### Post by cruzer001 on 2018-04-26
I just tried it on my 18.04 install, setup a new user with admin account.  It worked first try.

You did yours with the "user" gui?

---

### Post by sevendogsbsd on 2018-04-26
cigtoxdoc - are permissions and ownership on your "johnl" user somehow wrong? Using sudo, does the output of

```
ls -la /home/johnl
``` 

match what that command gives for your user "john"?

---

### Post by cigtoxdoc on 2018-04-26
Thank you for your suggestion.  sudo ls -la /home/johnl appears to give the same listing as ls -la /home/john .

How do I get out of this problem?

John

---

### Post by sevendogsbsd on 2018-04-26
What does the line for each user in "/etc/passwd" look like? The UID's will be different but are they similar to this:

```

exampleuser:x:1000:1000:Example R. User,,,:/home/example:/bin/bash

```

And you were successfully able to change the password for user "johnl"? So at the login screen, are there 2 users, "john" and "johnl"? If you try to login to the "johnl" user from the login screen, what happens?

---

### Post by cigtoxdoc on 2018-04-26
More here that I previously wrote.  /home/johnl contains much of my missing data for evolution.  So, the question is how to bail myself out of this problem.  Are the instructions at [https://linuxtechlab.com/rename-user-in-linux-rename-home-directory/](https://linuxtechlab.com/rename-user-in-linux-rename-home-directory/) correct?  John

---

### Post by sevendogsbsd on 2018-04-26
I believe so but I was trying to figure out why you can't login to your "johnl" user. If you could login to that user, you could just use that account. Are you considering renaming the account and trying to login then? 

Another option would be to copy all of the data from that user (johnl) to the current "john" account. I was just trying to make it easy by figuring out why you can't login. I believe the evolution files are under

```
~/.config
``` and/or
```
~/.local/share
```

but not 100% sure because I haven't used evolution in a while. You could use sudo from your "john" account and copy the "johnl" evolution files over if that works for you.

---

### Post by cigtoxdoc on 2018-04-26
Thank you, password data shown below

john:x:1000:1000:john,,,:/home/john:/bin/bash
johnl:x:1001:1001:johnl,,,:/home/johnl:/bin/bash

still need to retry login for johnl

---

### Post by cigtoxdoc on 2018-04-26
Thank you, password data shown below

john:x:1000:1000:john,,,:/home/john:/bin/bash
johnl:x:1001:1001:johnl,,,:/home/johnl:/bin/bash

still need to retry login for johnl

---

### Post by cigtoxdoc on 2018-04-26
When I login to johnl, the screen goes black for more than a few seconds, and then comes back with the login.  It appears that no desktop is being launched when I login as johnl.

What files control what happens after you login?  John

---

### Post by cigtoxdoc on 2018-04-26
Thank you, password data shown below

john:x:1000:1000:john,,,:/home/john:/bin/bash
johnl:x:1001:1001:johnl,,,:/home/johnl:/bin/bash

still need to retry login for johnl

---

### Post by cigtoxdoc on 2018-04-26
when I su johnl and work as johnl, I should be able to launch evolution from the command prompt.  However, I get:

john@john-Vostro-3500:~$ su johnl
Password: 
johnl@john-Vostro-3500:/home/john$ evolution
No protocol specified
Unable to init server: Could not connect: Connection refused
Failed to initialize gtk+: Cannot open display: 
johnl@john-Vostro-3500:/home/john$ 

You cannot launch a graphical application from johnl.  However, you can run sudo nano .xession-errors.  One line in that file is "cannot connect to brltty at :0"

It looks like johnl can do everything except lauch programs requiring the graphical user interface.

John

---

### Post by cigtoxdoc on 2018-04-27
This problem has been solved by reinstalling Ubuntu 18.04 and setting the user to johnl.

This pulled up all the e-mails that had not shown up with prior installation of 18.04

Thank you to all who replied with helpful suggestions

John

---

