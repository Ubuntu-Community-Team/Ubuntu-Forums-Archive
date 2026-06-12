---
title: "Confusion about root password?"
date: 2005-06-18
forum: Installation &amp; Upgrades
---

### Post by speedsix on 2005-06-18
Now I'm sure I'm just being stupid but.. I know you can't login as root via GDM but why can't I log into a console as root??

The install doesn't ask you for a root password and when I use 'sudo' it works with my user password?

This is different in Suse so I'm a little confused.

many thanks

---

### Post by desdinova on 2005-06-18
Its a way to discourage use of root - you shouldn't log in as root really, and use it only as and when.

If you look at [http://www.ubuntuguide.org](http://www.ubuntuguide.org) - it explains all this and how to re-enable the root password.

I came here from Suse - personally I think its one of Ubuntu's better ideas.

---

### Post by speedsix on 2005-06-18
Excellent thanks, that's makes sense.

---

### Post by speedsix on 2005-06-19
One more problem, I have created a user account for my wife and it won't accept her password at login, I can go to the 'users' section (asks for root password) and change it but it doesn't help... any ideas?

I may delete the user and create a new one for her.

Thanks

---

### Post by Worzel on 2005-06-19
I came from SuSE as well, and agree that it's safer not having a root user specifically set up.
Have a look at the man pages for useradd, userdel and usermod. If you're using Kubuntu from a cd installation be aware the Kuser programme is faulty - I tried several times to add my wife as a user before I found out. It may have been fixed since but I've not used it.
HTH
Jim

---

### Post by mmealman on 2005-06-19
[QUOTE=speedsix]One more problem, I have created a user account for my wife and it won't accept her password at login, I can go to the 'users' section (asks for root password) and change it but it doesn't help... any ideas?

I may delete the user and create a new one for her.

Thanks[/QUOTE]

System->Administration->Users and Groups should be asking you for your password, not the root password.

Another trick, if you want a root shell prompt simply use: sudo -i

---

### Post by speedsix on 2005-06-19
Ah I see it all makes sense now, basically sudo is giving specified users super user rights, not actually logging you in as a 'root' user.


I'm still struggling trying to get a working secondry account alongside mine for my wife. I've tried deleting and re-adding here account, changing her password but I cannot login console or gdm with her name??

I'm using system>admin>users and groups


thanks

---

