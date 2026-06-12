---
title: "Warning: Firefox Upgrade Failure"
date: 2018-09-28
forum: Installation &amp; Upgrades
---

### Post by slow-speed on 2018-09-28
I just ran the upgrade to Firefox because of the notification I received this morning.  However, every single open tab displays a blank page.

Luckily I was able to recover by going to /var/cache/apt/archives and finding the old version there.  I then copied the full name into the command:
sudo dpkg -i "packagename"
where it says "packagename", and ran it in a terminal.  I  had no problem with using the quotes, although that is normally not done.

  Everything is now back to where it was.  Hope this helps someone else, since sadly the package managers do not have any help on this.

Xubuntu 14.04, Firefox ESR and Firefox Quantum

---

### Post by deadflowr on 2018-09-28
Which one failed the esr or the quantum?
Note that Firefox ESR has never been an official package in Ubuntu and has no repository package.

(There is a snap version of Firefox ESR, but on 14.04 you need to install snapd and it would never notify you of updates as 14.04 does not use the newer Ubuntu Software store,
which does have update notifications available. Aside from the fact that snaps update automatically in the background and are not ever listed among software updates in general...)

---

### Post by ajgreeny on 2018-09-28
You should also update your OS if possible as Xubuntu LTS versions have only 3 years support, not 5 years, so the specific Xubuntu parts of your Xubuntu-14.04 system may not have been updated for over 2 years which is a potential security risk.
I accept that a lot of the OS packages from the standard repos will still be updated for a few more months (until April 2019) but I would be feeling unsafe if in your situation.

What version of FF are you running when you see this warning?

---

### Post by slow-speed on 2018-09-28
@ deadflowr:
Thanks.
> Which one failed the esr or the quantum?
Note that Firefox ESR has never been an official package in Ubuntu and has no repository package.

ESR
And if it is not supported, why does it get updated?  Is it from a non-Xubuntu repo?


@ ajgreeny:
If the OS version is no longer supported, I should have received a notification to that affect.

---

### Post by deadflowr on 2018-09-28
> ESR
And if it is not supported, why does it get updated? Is it from a non-Xubuntu repo?
It's available through Ubuntu's mozilla-team ppa:
[https://launchpad.net/~mozillateam/+archive/ubuntu/ppa?field.series_filter=trusty]("https://launchpad.net/~mozillateam/+archive/ubuntu/ppa?field.series_filter=trusty")
as well as this other ppa:
[https://launchpad.net/~jonathonf/+archive/ubuntu/firefox-esr?field.series_filter=trusty]("https://launchpad.net/~jonathonf/+archive/ubuntu/firefox-esr?field.series_filter=trusty")

But ppas are unofficial package archives.
Where 3rd parties can upload packages, as well as Ubuntu developers can upload testing packages.

Any added ppa archive to your system will automatically update along with all other updates.

Edit:
Adding a community discussion on it here:
[https://discourse.ubuntu.com/t/firefox-esr-package-is-really-needed/1970]("https://discourse.ubuntu.com/t/firefox-esr-package-is-really-needed/1970")

---

### Post by slow-speed on 2018-09-28
Thanks.

---

