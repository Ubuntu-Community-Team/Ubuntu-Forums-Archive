---
title: "Upgrading 10.04"
date: 2015-02-20
forum: Installation &amp; Upgrades
---

### Post by Langstracht on 2015-02-20
I am STILL running 10.04.  Yes, I know, I know.

However, now having finally bellied up to the upgrade bar, I have a problem.

The Update Manager returns the following (error) message:

> Could not calculate the upgrade

An unresolvable problem occurred while calculating the upgrade.

Please report this bug against the 'update-manager' package and include the following error message:
'E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.'

That said, it would "appear" that the Upgrade (to 12.04) IS operational.

The question is, can i go ahead with it?  Or am I just asking for trouble?

If the latter, any pointers on how I might fix the "problem" would be most appreciated.

TIA

---

### Post by bapoumba on 2015-02-20
Do you have a separate partition for /home and personal files ? Best would be to fresh install. 14.04 if you want a LTS, 14.10 or the upcoming 15.04 if not.
In any case, back up anything you'd cry if you'd loose.

---

### Post by grahammechanical on 2015-02-20
It can be done but the simple way was to upgrade before Ubuntu 10.04 desktop reached end of life. The 10.04 desktop repositories are now closed. They have been put into an archive. They are still accessible but you will need to edit the /etc/apt/sources.list file and change the URL of all the relevant repositories to use old-releases.ubuntu.com for whatever is there at present. On my machine it is gb.archive.ubuntu.com

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

Remember, There is a massive difference in code between 10.04 and 12.04. The complete look of the User Interface is different. The Gnome desktop environment is different. Gnome 2 DE is replaced with Gnome 3 DE. Success is not assured.

Regards.

---

### Post by tokyobadger on 2015-02-21
Do you know if your hardware will support a newer version of Ubuntu? Might be good to list your hardware specs first

---

