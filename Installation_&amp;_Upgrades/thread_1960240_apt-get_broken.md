---
title: "apt-get broken"
date: 2012-04-17
forum: Installation &amp; Upgrades
---

### Post by greatpowerofcheese on 2012-04-17
Hello, I'm running Ubuntu 11.10 and today I've been experiencing problems with apt-get.

I rebooted my computer and when I logged in, there was a little red icon in the top right saying that my package manager was somehow broken.  It said to run apt-get to see what the problem was.  When I did, it complained about /var/lib/dpkg/status.

I did some searching and it was suggested to use status-old instead.  That did not work.  Here are the contents of status:

```
#! /bin/sh

set -e

case "$1" in
    remove|disappear)
    if which update-mime >/dev/null;
    then
            update-mime
    fi
        ;;
    upgrade|failed-upgrade|purge|abort-install|abort-upgrade)
        ;;
    *)
        echo "prerm called with unknown argument \`$1'" >&2
        exit 1
    ;;
esac
```

The contents of /var/lib/dpkg/status-old were equally invalid (and subsequently overwritten by incremental success), but I eventually restored status with the newest backup from /var/backups/dpkg.status.1

That got me to the next error, this time about /var/lib/dpkg/diversions:

```
#!/bin/sh
set -e

# Automatically added by dh_python2:
if which pyclean >/dev/null 2>&1; then
	pyclean -p language-selector-gnome 
else
	dpkg -L language-selector-gnome | grep \.py$ | while read file
	do
		rm -f "${file}"[co] >/dev/null
  	done
fi

# End automatically added section
```

I fixed that problem by replacing it with diversions-old, but now when I run sudo-apt-get upgrade, I get the following error:

> dpkg: unrecoverable fatal error, aborting:
 conflicting diversions involving `/# $Id: Script.pm,v 2.7 2004/06/10 21:19:34 neilb Exp $' or `/#'
E: Sub-process /usr/bin/dpkg returned an error code (2)

What could have caused this systematic error in this computer's package manager?  Why were status and diversions replaced with scripts?  Can this be solved?

Thank you very much,
Steven

---

### Post by albandy on 2012-04-17
Usually there is a backup of the last status in /var/backups/dpkg.status.0 so try doing this:

sudo cp /var/backups/dpkg.status.0 /var/lib/dpkg/status

Also move /var/lib/dpkg/diversions to your home and make an empty the file.

sudo mv /var/lib/dpkg/diversions ~/diversions.backup
sudo touch /var/lib/dpkg/diversions

then try to install some package. If fails do the following:
dpkg --configure -a

---

### Post by greatpowerofcheese on 2012-04-17
Yeah, that makes sense..but it isn't quite working.

I tried copying over dpkg.status.0, but it didn't change anything. I also tried unzipping dpkg.status.1.gz and replacing status with that too, but again, no luck.  Still stuck with

>  dpkg: unrecoverable fatal error, aborting:
 conflicting diversions involving `/# $Id: Script.pm,v 2.7 2004/06/10 21:19:34 neilb Exp $' or `/#'
E: Sub-process /usr/bin/dpkg returned an error code (2)

---

### Post by greatpowerofcheese on 2012-04-17
Clearing diversions seems to have worked.  I'm just waiting for an extremely slow adobe-flashplugin update.  

Thank you, albandy!

---

