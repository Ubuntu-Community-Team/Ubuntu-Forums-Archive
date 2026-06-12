---
title: "How do i confirm that the upgrade to 12.04 was complete"
date: 2012-05-06
forum: Installation &amp; Upgrades
---

### Post by vanuda on 2012-05-06
I noted that after the upgrade from 11.10 to 12.04 that seemed to go well that i still was on kernel 3.0..

Ok. Manually upgraded to 3.2 which was done without any complaints from the system..

But.. How do i confirm that the rest of the system is updated?

Can i reset the apt system so that it rechecks all individual packages are checked
against the package versions that 12.04 should contain?

Currently i get the message that everything is updated...
( actually python-central just got a small update.. )

Any suggestions ( except reinstall..;-)

---

### Post by grahammechanical on 2012-05-06
Go to the power/cog menu and select Software Updater to open the Update Manager.

Click on Settings and go to the Updates tab and see if your software sources (repositories) are listed for Precise and not Oneiric.

Open a terminal and run this code

```
 lsb_release -a
```

and see if the release is Precise or Oneiric

Regards.

---

### Post by ajgreeny on 2012-05-06
Command ```
lsb_release -a
``` in terminal will tell you.

---

### Post by vanuda on 2012-05-07
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 12.04 LTS
Release:        12.04
Codename:       precise

This was still the output when running on kernel 3.0 that i manually
had to upgrade to 3.2..

---

### Post by vanuda on 2012-05-07
So the question is still

How do i confirm that all packages are upgrades to precise 12.04 LTS since at least
the kernel package stayed on 3.0..

---

### Post by arpanaut on 2012-05-07
try: ```
 sudo apt-get update && sudo apt-get dist-upgrade
```

and see if it wants to bring in anything else.
Sometimes update manager gets finiky dist-upgrading if there are packages to be removed.
before allowing the upgrade please look for any package removals that don't look right.
Post here if it is not obvious if the removals are safe

There are times that the release upgrade does not complete the "clean-up" correctly afterwards 
so manual clean-up is necessary.

If nothing out of sorts appears with that command then you should be good to go.

---

### Post by vanuda on 2012-05-07
Yep.. Tried this as well both with kernel 3.0 which did not give any packages to update as well as with 3.2..

The only thing that popped up after a few hours was the python-central that for some reasons was ready for a small update..

---

