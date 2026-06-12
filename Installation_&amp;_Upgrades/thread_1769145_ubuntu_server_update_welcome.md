---
title: "ubuntu server update welcome ?"
date: 2011-05-27
forum: Installation &amp; Upgrades
---

### Post by Sorcerer25 on 2011-05-27
hi !

> 
Ubuntu 10.04.2 LTS

Welcome to Ubuntu!
 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)

36 packages can be updated.
20 updates are security updates.
i just did an update using aptitude, and then restarted server
i still get this message and aptitude cannot find any package that can be updated

so, why i still get this message when i log in ?

---

### Post by mörgæs on 2011-05-28
Hi, welcome to the fora.

You could try to boot the computer and run

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

Please post the error messages, if any.

---

### Post by Sorcerer25 on 2011-05-28
thank you ! ... for the interest

i just dig it up :)

seems like i just found 3 problems ... ubuntu problems ...

1. real problem is that motd.tail is not properly updated ... in  /etc/update-motd.d/90-updates-available there is a:

/usr/lib/update-notifier/apt-check --human-readable

and if i run it i get:
> 
 /usr/lib/update-notifier/apt-check --human-readable
0 packages can be updated.
0 updates are security updates.

so, starting scripts ignore that file completely !

2. this is also really wrong:
> 
Ubuntu 10.04.2 LTS

Welcome to Ubuntu!
 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)
reading /etc/update-motd.d/10-help-text
> 
#!/bin/sh

if uname -r | grep -qs "\-server"; then
        echo
        echo "Welcome to the Ubuntu Server!"
        echo " * Documentation:  http://www.ubuntu.com/server/doc"
else
        echo
        echo "Welcome to Ubuntu!"
        echo " * Documentation:  https://help.ubuntu.com/"
fi
and this is big be cause ...
> 
uname -r
2.6.32-31-generic-pae
i did installed ubuntu server !

3. i installed package update-motd
> 
cat /usr/share/doc/update-motd/README
update-motd
=============

See the manpage: update-motd(1).

 $ man 1 update-motd
where is that utility ?
> 
dpkg -L update-motd       
/.
/etc
/etc/update-motd.d
/usr
/usr/share
/usr/share/doc
/usr/share/doc/update-motd
/usr/share/doc/update-motd/README
/usr/share/doc/update-motd/THANKS
/usr/share/doc/update-motd/copyright
/usr/share/doc/update-motd/changelog.Debian.gz
there is not file named "update-motd" that in the whole ubuntu acording to:

[http://packages.ubuntu.com/search?searchon=contents&keywords=update-motd&mode=exactfilename&suite=natty&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=update-motd&mode=exactfilename&suite=natty&arch=any)


this is just some wrong messages so is not a big deal and i don't know where or how to move it, but this is no longer "i need help" topic

[B]This is an obvious Ubuntu system problem, it should be solved by packages/distribution level !

[/B](not hacked by myself :) )

---

### Post by Old_Grey_Wolf on 2011-05-28
I'm not sure this will help; however, try the following command```
sudo apt-get dist-upgrade
```rather than sudo apt-get upgrade.

sudo apt-get upgrade
This command installs the latest versions of any out-of-date packages on your system. It never installs a package that is not yet installed.

sudo apt-get dist-upgrade
This command installs up-to-date version of packages, and may install additional packages.

---

### Post by Sorcerer25 on 2011-05-28
nope, it won't !

if you read my second post you will see that this is no longer an apt/system update/upgrade problem ... whatsoever

also, upgrade/distupgrade, etc. does nothing if you have already have a top version release !

ubuntu server 10.04.02 is the latest LTS release

thank you for interest, but (sorry to say this) **read before post**

---

### Post by Old_Grey_Wolf on 2011-05-28
> **Sorcerer25 said:**
> nope, it won't !

if you read my second post you will see that this is no longer an apt/system update/upgrade problem ... whatsoever

also, upgrade/distupgrade, etc. does nothing if you have already have a top version release !

ubuntu server 10.04.02 is the latest LTS release

thank you for interest, but (sorry to say this) **read before post**

OK, then good luck getting your problem fixed.

---

### Post by tgalati4 on 2011-05-28
It's a known bug.  Delete /etc/motd.tail and next time you boot it should reflect your package update status.

---

