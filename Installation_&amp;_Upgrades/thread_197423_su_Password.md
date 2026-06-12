---
title: "su Password"
date: 2006-06-15
forum: Installation &amp; Upgrades
---

### Post by asearle on 2006-06-15
I've just installed 6.06 on my old Acer Travelmate 333 and EVERYTHING works.  I can't believe it :-)

The only problem that I have is that I have no root password.  It was not requested during set-up so I assume there is a default one.  I've tried a whole stack of obvious ones and have googled the web but somehow I can't find it.  And I really need it now to fix a synaptic session.

I hope someone can help me?

Many thanks,
Alan Searle

[email]aj_searle@xxxxxxyahoo.com[/email]

---

### Post by bruce89 on 2006-06-15
su is not the way it is done in Ubuntu, we use sudo.  The root password is a random string of characters.

---

### Post by fritz_monroe on 2006-06-15
Ubuntu uses sudo for admin tasks.  The root user is not enabled by default.  If you need to set the password, you can do a

> sudo passwd root

At least that's the way I remember it from about 6 months ago.

---

### Post by Jasper Houtman on 2006-06-15
You can set it up and you have to activate your root account in "users and groups" (system > administration).

Though it is better to just run the sudo command in the terminal (much safer)

---

### Post by givré on 2006-06-15
The reasons : [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by glotz on 2006-06-15
It asked you for one password during the install. That's the only password. The one you login with.

Ubuntu does have a very nice h/w detection... :)

---

### Post by asearle on 2006-06-16
Fantastic!  Yes, now I understand the reason for sudo.  It sounds well-thought out.

And I used the sudo comand to fix my synaptic problem.  Many thanks for the quick and comprehensive responses.

Regards,
Alan.

---

