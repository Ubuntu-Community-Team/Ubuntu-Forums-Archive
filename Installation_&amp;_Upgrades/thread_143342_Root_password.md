---
title: "Root password"
date: 2006-03-12
forum: Installation &amp; Upgrades
---

### Post by beforewisdom on 2006-03-12
Hi;

It was early this morning that I installed ubuntu to my hard drive, but I can't recall being prompted for a root pasword.

I can't sudo as "root".   

Now that the system is intalled to my hard drive, is there anyway I can set up, or change my root password.....not having the root password?

Thanks 

Steve

---

### Post by 5-HT on 2006-03-12
Hi, this link may be of help: [https://wiki.ubuntu.com/RootSudo]("https://wiki.ubuntu.com/RootSudo")
It discusses why the root account is locked by default, how you can use sudo to obtain root priviledges, and how you can set up your root account if you'd really like to.

Just wondering about you mentioning not having set a password...did you set up a user account name/password and just not a root password?

If so, that is the password you'd use for sudo (the link talks about this).

If you are having a problem with sudo itself, that is another issue alltogether.
If you did an expert install, your user will not have been added to the sudoers file.
The link says how you can add yourself to the file to correct this.


HTH

---

### Post by knalle on 2006-03-12
try this to get the root password for a ubuntu breezy installation:

less /var/log/installer/cdebconf/questions.dat

and scrolldown to the word "password"

Happy Hacking!

---

### Post by beforewisdom on 2006-03-12
Okay, I did notice that I don't need it.  As long as I can do what I need to do with sudo I am fine.

Thanks!

Steve

---

