---
title: "password management"
date: 2005-05-09
forum: Installation &amp; Upgrades
---

### Post by Ted Catchpole on 2005-05-09
I've just successfully my first Ubuntu installation (Hoary on an AMD64 machine).
I hope this is the right place to ask for help. Sorry if not.

I can log in as me successfully, but
(a) when I try to add a new user, they can't log in - they just get an "incorrect password" message. In fact, when I check the user details, the password (shown as asterisks) doesn't even have the same number of characters as I've just set it. This happens whether I manually type in a password or just generate one;
(b) a lot of users are generated automatically - e.g., root. But their password are unknown to me. Can I find out what they are (or change them after solving the previous problem)?

Thanks for any help.

Ted.

---

### Post by lt_kije on 2005-05-09
> **Ted Catchpole]I've just successfully my first Ubuntu installation (Hoary on an AMD64 machine).
I hope this is the right place to ask for help. Sorry if not.[/QUOTE]

You're in the right place -- congrats on the install (and the machine)!

[QUOTE=Ted Catchpole]I can log in as me successfully, but
(a) when I try to add a new user, they can't log in - they just get an "incorrect password" message. In fact, when I check the user details, the password (shown as asterisks) doesn't even have the same number of characters as I've just set it. This happens whether I manually type in a password or just generate one said:**
> 

Are you using the graphical interface to create new users? If you can't get that to work, try making a user (or modifying their password) on the command line -- if you're not comfortable with this, don't worry. In case you're interested, however:

$ sudo adduser NEWUSER
$ sudo passwd NEWUSER

The first command will create a new user with the name "NEWUSER"; the second will modify the password for an existing user.

[QUOTE=Ted Catchpole](b) a lot of users are generated automatically - e.g., root. But their password are unknown to me. Can I find out what they are (or change them after solving the previous problem)?

You shouldn't need to use those accounts; they're for special purposes (eg www-data is a limited user which is used ONLY for running a webserver; regular humans never log in as www-data or other special accounts).

Other Linux distributions use root as the system superuser. In Ubuntu, root is disabled (see [http://www.ubuntulinux.org/wiki/RootSudo](http://www.ubuntulinux.org/wiki/RootSudo) for more info).

HTH,
lt_kije

---

### Post by Ted Catchpole on 2005-05-10
[QUOTE=lt_kije]
Are you using the graphical interface to create new users? If you can't get that to work, try making a user (or modifying their password) on the command line -- if you're not comfortable with this, don't worry. In case you're interested, however:

$ sudo adduser NEWUSER
$ sudo passwd NEWUSER

The first command will create a new user with the name "NEWUSER"; the second will modify the password for an existing user.[/QUOTE]

Yes, this worked perfectly, although I needed to know the exisiting password for NEWUSER. Thanks very much for this solution.

I was trying to accomplish the same thing using System -> Administration -> Users and Groups -> Add user, but it looks like this must be buggy on Hoary for AMD64. I'll try to submit this as a bug.

Ted.

---

### Post by lt_kije on 2005-05-10
[QUOTE=Ted Catchpole]I read somewhere (Linux Format?) that  the root account is disabled *by default,* but that it can be enabled, for those people who like doing sys-admin the old-fashioned way  ;-)[/QUOTE]

Sure, you can enable it. I work as an admin in two environments, one using sudo, the other root. I find root to be inconvenient -- always logging in, logging out. Sudo allows me to hop into superuser access just for the task at hand; I can also tweak superuser power for other users. In my experience, sudo is a great tool. If you really want to use su (beyond eg sudo su), there're a couple (really long) threads elsewhere in the forums here. :-)

Good luck,
lt_kije

---

### Post by Ted Catchpole on 2005-05-10
[QUOTE=lt_kije]Sure, you can enable it. I work as an admin in two environments, one using sudo, the other root. I find root to be inconvenient -- always logging in, logging out. Sudo allows me to hop into superuser access just for the task at hand; I can also tweak superuser power for other users. In my experience, sudo is a great tool. If you really want to use su (beyond eg sudo su), there're a couple (really long) threads elsewhere in the forums here. :-)

Good luck,
lt_kije[/QUOTE]

OK. I've just (belatedly) read the Wiki entry on sudo. I'm convined. I'll give it a try.
Thanks again for the help.   
Ted.

---

