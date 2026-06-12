---
title: "How do I upgrade from x64 15.04 to 15.10?"
date: 2016-01-09
forum: Installation &amp; Upgrades
---

### Post by fr33z0n3r on 2016-01-09
I have not seen any indicator in Software Updater indicating the upgrade is available...is it still possible to perform this upgrade method as of Jan 1 2016?

I don't seem to have any issues, but I'm no expert.  There is one 3rd party app (owncloud client)  I am not upgrading due to issues.  I can't believe that would prevent the upgrade?

---

### Post by grahammechanical on 2016-01-09
I do not think that 15.04 will reach end of life until the end of January this year. And even then I do not think that the maintainers are quick to close the 15.04 repositories.

What setting do you have in System Settings>Software & Updates>Updates tab? What is "Notify me of a new Ubuntu version" set to? Is it set to "For any new version?" That is the setting you need. Then start an update and see what you are offered when you run Software Updater from the Dash.

Regards

---

### Post by fr33z0n3r on 2016-01-09
the settings are correct.  I even tried altering them to "reset" them to no avail.

---

### Post by deadflowr on 2016-01-09
Run the manual update commands from a terminal:
```
sudo apt-get update
sudo apt-get upgrade
```
are there any errors?

---

### Post by shane_faulkinbury2 on 2016-01-09
deadflower's recommendation should work, but you also might try [COLOR=#111111][FONT=Consolas]sudo apt-get dist-upgrade[/FONT][/COLOR]

---

### Post by fr33z0n3r on 2016-01-09
> **deadflowr said:**
> Run the manual update commands from a terminal:
```
sudo apt-get update
sudo apt-get upgrade
```
are there any errors?

No errors, but I am NOT upgrading the app that is listed.  I don't know why it would have an impact on an Ubuntu upgrade.

```
user@host:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... The following package was automatically installed and is no longer required:
  libneon27
Use 'apt-get autoremove' to remove it.
Done
The following packages will be upgraded:
  libowncloudsync0 libqtkeychain0 owncloud-client owncloud-client-l10n
4 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,637 kB of archives.
After this operation, 168 kB of additional disk space will be used.
Do you want to continue? [Y/n] n
Abort.


```

---

### Post by Dennis N on 2016-01-09
If your settings are to notify for any new version, then at the conclusion of any regular update you perform, you get the advisory in the attached screen shot - then (obviously) click on the "Upgrade..." button. 

Maybe I misunderstand what you want, but if you are trying to _not_ upgrade one package and upgrade the rest of the distro to 15.10, I would suspect that may not be possible due to compatability problems.

NOTE: The message of the screen shot will be presented when you start "software updater" even if the system is already up to date.

---

### Post by fr33z0n3r on 2016-01-09
> **Dennis N said:**
> If your settings are to notify for any new version, then at the conclusion of any regular update you perform, you get the advisory in the attached screen shot - then (obviously) click on the "Upgrade..." button. 

Maybe I misunderstand what you want, but if you are trying to _not_ upgrade one package and upgrade the rest of the distro to 15.10, I would suspect that may not be possible due to compatability problems.

NOTE: The message of the screen shot will be presented when you start "software updater" even if the system is already up to date.

I believe that could be the reason also, any idea how I get my issue rectified? do I open a bug for my inability to upgrade?

Honestly I haven't done anything too weird with my install but it may be possible that previous kernel patching issues have caused this. 

I need to know how to actually move forward given this.

UPDATE- re reading your post, I think you are saying you think this 3rd pay app is causing the issue. I'll consider performing the update, but I need to obtain the deb first.

---

### Post by Dennis N on 2016-01-09
You may need to continue what you aborted, and upgrade those 4 packages shown in post #6 first so that the system is up-to-date.

Then, are you offered an Upgrade by the Software Manager?

---

### Post by fr33z0n3r on 2016-01-10
well, that did in fact permit the upgrade to be advertised. 

And now, I have a new issue, potentially.  The upgrade crash mid-process.  The screen was frozen and unresponsive.  I hard booted it.  The Software Updater ran more stuff automatically and then said it was up to date.  

WTF Canonical?  This is the 2nd upgrade in a row that has failed on me.   QA doing downhill.

BUG: unable to handle kernel paging request at 00000000fffffffc

---

