---
title: "Kerberos installation fails"
date: 2013-01-15
forum: Installation &amp; Upgrades
---

### Post by red123nax on 2013-01-15
Hello,

I tried to install Kerberos using the following commands:
```
sudo apt-get install krb5-kdc
sudo apt-get install krb5-admin-server
```But when I try to I natal it gives me the message that krb5-user, and some other krb5-programms are missing.

When I tried to install them with apt-get it can't be found.
```
Reading package list... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 krb5-kdc : Depends: libverto1 but it is not installable
            Depends: krb5-config but it is not installable
            Depends: krb5-user but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```I'm thinking it has something to do with the repositories.

Can anybody help me?

Thanks in advance !!

BTW I'm talking about the x64 server version of Ubuntu.

---

### Post by red123nax on 2013-01-17
I already got it.
The problem what that i had to issue the apt-get upgrade and apt-get update commands.

---

