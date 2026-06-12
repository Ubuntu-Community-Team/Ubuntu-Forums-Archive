---
title: "set user instead of root in postinstall-script"
date: 2011-10-03
forum: Installation &amp; Upgrades
---

### Post by Mar2zz on 2011-10-03
Hi there, new poster, lurker for years...
I have written a bashscript that creates .deb-files for github-applications (like sickbeard, couchpotato and others).

With the postinstall script I am trying to set one last variable in the initscripts, the username of the user that is installing. But it sets root as installing user (dpkg does that).

The postinstallscript:
```
#!/bin/sh

set -e

# change values in init.script
if grep -i 'SICKBEARD_USER' /etc/init.d/sickbeard > /dev/null
    then
    sed -i "s!SICKBEARD_USER!$USER!g" /etc/init.d/sickbeard
fi

#create pidfile permissions
if ! [ -d /var/run/sickbeard ]
    then
    mkdir /var/run/sickbeard
fi
chown -R $USER /var/run/sickbeard

#create datadir permissions
if ! [ -d ~/.sickbeard ]
    then
    mkdir ~/.sickbeard
fi
chown -R $USER ~/.sickbeard

# execute init.script
chmod +x /etc/init.d/sickbeard
update-rc.d sickbeard defaults
/etc/init.d/sickbeard start
```

When I install this app, it installs fine, with no errors, and the application also works. But $USER is replaced with root, and I want it to be replaced with the username of the user that executes the debfile (like sudo dpkg -i sickbeard-11.10.3-ALL.deb or with software-centre). The weird thing is that ~/.sickbeard is translated into the home-directory of the user installing. So dpkg is aware of that user, but doesn't change the variable to that user.. How come?

If I can solve this I can setup a repo and upgrade these apps from the repo (the bashscript that writes the .deb-files can be run from cron and I hope I can maintain a repo that way with weekly cronjobs).

I googled a lot on this, but couldn't find a solution. So maybe this is impossible? (hope not)

---

### Post by Mar2zz on 2011-10-05
Allready solved. Well not by using the username of the person that is installing, but with creating a special dedicated user to run sickbeard, with a homedirectory in /etc/sickbeard.

---

