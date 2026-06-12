---
title: "root password"
date: 2005-02-11
forum: Installation &amp; Upgrades
---

### Post by alexj on 2005-02-11
Sorry, something silly. I have installed ubuntu, entered my user name and my password, completed registration, loged in. How can I "su"? I don't remember entering root password at any time.

Thanks

---

### Post by bigkahuna on 2005-02-11
The root password is the same as your user password.  If you want to change it, instructions to do so are here:

[http://ubuntuguide.org/](http://ubuntuguide.org/)

---

### Post by Hendrin on 2005-02-11
You don't use su in Debian/Ubuntu.

Use "sudo".

For instance: 
sudo vi document.txt

Will run vi as a superuser to view that document.  Now there is absolutely no reason to do so, but I used it as an example. :)

 and checking out the guide linked above is also a great idea.

---

### Post by grj on 2005-02-11
You can also do this

sudo su
Password: enter password

You will now be running as super-user.

---

### Post by bigkahuna on 2005-02-11
[QUOTE=Hendrin]You don't use su in Debian/Ubuntu...[/QUOTE]

Really?  I've used it a number of times and it worked.  I'm a newbie, and maybe just don't know any better, but su worked for me on my Warty install.  When you type "su" you're prompted to enter your password, then the prompt changes so you're now the root...

---

### Post by Hendrin on 2005-02-11
Well, I'm a newbie to. :)

Sadly, whenever I tried to use su, it always requested a password which my normal one for account wouldn't work with.

sudo su does work, thanks for pointing that out. :)

---

### Post by k.ODOMA on 2005-02-12
[QUOTE=Hendrin]You don't use su in Debian/Ubuntu.[/QUOTE]

Has this changed for Debian in the last 2 months? That was the last time I ran it and sudo was not default, su was.

---

