---
title: "Installation user"
date: 2007-02-22
forum: Installation &amp; Upgrades
---

### Post by imatwork on 2007-02-22
I rarely create a second account after installing Ubuntu. Recently I have though.

It appeared as though the second account was locked down more-so than the account created during installation.

One obvious difference was being unable to use a sudo password in the secondary account unlike the default installation account. 

Questions:
What would the sudo password be for the second account(?): The password for the primary (default install account), or the password created for the second account?

Is it best practice to **not** use the account created during installation in favor of creating a post-install, secondary account?

---

### Post by Kateikyoushi on 2007-02-22
I have only one user on my notebook and never felt I would need one more.

The password should be what you set for the user, so for the second the second one's.

---

### Post by louieb on 2007-02-22
In order for the second, third ... user to use sudo they have to be a member of the admin group.

---

### Post by Catsworth on 2007-02-22
> **louieb said:**
> In order for the second, third ... user to use sudo they have to be a member of the admin group.

Ummm....

Correct me if I'm wrong.....but I don't think that's entirely correct - I seem to recall that the user _also_ needs to be a member of the *adm* group.

---

### Post by bapoumba on 2007-02-22
> **Catsworth said:**
> I seem to recall that the user _also_ needs to be a member of the *adm* group.
```
~ $ sudo cat /etc/sudoers
Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

```
see **man sudoers** or [http://www.die.net/doc/linux/man/man5/sudoers.5.html]("http://www.die.net/doc/linux/man/man5/sudoers.5.html") ;)

edit: adm was historically to read log files, I think... Will check on that.
edit 2: [http://www.linuxsecurity.com/resource_files/host_security/securing-debian-howto/ch8.en.html]("http://www.linuxsecurity.com/resource_files/host_security/securing-debian-howto/ch8.en.html")
> adm: Group adm is used for system monitoring tasks. Members of this group can read many log files in /var/log, and can use xconsole. Historically, /var/log was /usr/adm (and later /var/adm), thus the name of the group.

---

### Post by imatwork on 2007-02-23
Thank you for the information. I will look into this more over the weekend.

---

