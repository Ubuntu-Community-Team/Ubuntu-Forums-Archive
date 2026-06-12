---
title: "Can't upgrade from Ubuntu server 13.04 to Ubuntu server 13.10"
date: 2014-03-16
forum: Installation &amp; Upgrades
---

### Post by Iznougoud on 2014-03-16
I've been running Ubuntu server since 11.04, and continously upgraded with every new version avilable. In retrospect, however, 13.04 proved to be a mistake for two reasons; I didn't really need it at the time, and I can't seem to upgrade beyond it.

During upgrade (command line; do-upgrade-release -d), I get a number of minor warnings. The most memorable being that Apache2 can't be restarted due to a config test failure. At the end of the upgrade, however, the entire process is abruptly terminated leaving me with the message "system error: E: Sub-process /usr/bin/dpkg returned error code 1" and a partially working and entirely unstable system.

Now I can't make heads or tails of this. I have tried upgrading more than once, bearing the hope that this bug - because that's what I think it is - has been rectified. And every single time, I've had to restore the installation from my backup. For now, this is annoying, but eventually it will leave me with an increasingly unusable installation of Ubuntu server unless I do a fresh install (which I have no desire to do) since upgrading to 13.10 obviously will be a prerequisite for any future versions.

Any advice would be greatly appreciated.

---

### Post by Iznougoud on 2014-03-18
Bump..?

---

### Post by claracc on 2014-03-18
Ubuntu 13.04 reached its end of life support 27 January, for this reason, the repositories may be removed from the server and you cannot upgrade this way. You will have to address your sources.list file to old-release repositories.

Please, see this link [http://askubuntu.com/questions/91815/how-to-install-software-or-upgrade-from-old-unsupported-release](http://askubuntu.com/questions/91815/how-to-install-software-or-upgrade-from-old-unsupported-release), specially comment 7, where I think you will have to substituted the given example karmic by Raring.

Other links which can help: 

[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)
[https://help.ubuntu.com/community/SaucyUpgrades](https://help.ubuntu.com/community/SaucyUpgrades)
[http://www.westernwillow.com/cms/blog/franco/upgrading-old-or-end-life-eol-release-ubuntu-back-usefulness](http://www.westernwillow.com/cms/blog/franco/upgrading-old-or-end-life-eol-release-ubuntu-back-usefulness)

---

### Post by Iznougoud on 2014-03-18
> **claracc said:**
> Ubuntu 13.04 reached its end of life support 27 January, for this reason, the repositories may be removed from the server and you cannot upgrade this way. /---/

Thank you for your reply and the links you provided. They will most certainly come to good use when I try to upgrade the next time.

Before I attempt another upgrade I would however need to address the main problem - that the upgrade fails for reasons the nature of which I have yet to determine. The message "system error: E: Sub-process /usr/bin/dpkg returned error code 1" is the only clue offered as to what's happened. A problem present ever since Ubuntu 13.10 was presented to the public some time back, and hence as such not the result of lack of support nor closed repositories. 

Should you (or anyone else for that matter) have any theories on this, pray tell. If not, once again thank you for your reply and the links :)

Update:

[I]A closer look at the log files reveals that Mumble-Django is somehow involved

"2014-03-18 22:40:35,147 ERROR got an error from dpkg for pkg: 'mumble-django': 'subprocess installed post-installation script returned error exit status 1'
2014-03-18 22:40:35,148 DEBUG running apport_pkgfailure() mumble-django: subprocess installed post-installation script returned error exit status 1
2014-03-18 22:56:06,361 ERROR not handled exception:
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1)

2014-03-18 22:56:06,363 DEBUG enabling apt cron job
2014-03-18 22:56:06,653 ERROR SystemError from cache.commit(): installArchives() failed"

Does anyone have any further info on this..?
[/I]

---

### Post by claracc on 2014-03-19
Could these two threads help?:

[http://ubuntuforums.org/showthread.php?t=1642173](http://ubuntuforums.org/showthread.php?t=1642173)
[http://askubuntu.com/questions/370620/e-sub-process-usr-bin-dpkg-returned-an-error-code-1-bug](http://askubuntu.com/questions/370620/e-sub-process-usr-bin-dpkg-returned-an-error-code-1-bug)

---

### Post by Iznougoud on 2014-03-19
As it turned out, the answer was to remove *mumble-django* before upgrading. A few other hickups occured such as *Apache2 *refusing to restart, but that was easily resolved by creating the (empty) file */etc/apache2/httpd.conf**. *For now everything seems to run relatively smoothly under 13.10, and hopefully there won't be any unpleasant surprises further down the line.

Once again. Thanks for your kind assistance. And if this solution in some small way can assist someone else in the same predicament, all the better.

*Well, one shouldn't expect things to run all too smoothly. Seems Apache2 2.4 has some issues with authorization using .htaccess - giving me an internal server error when I try to access any password protected site hosted on said server. The log turns up *".htaccess: AuthUserFile not allowed here" - *which is informative. In its own minimalistic way. Any info on this would be most appreciated. Worked perfectly before the upgrade.*
[I][B]
Edit 2: Although not explaining Apache 2.4's sudden refusal to use .htaccess-files, the solution is to remove them entirely and use /etc/httpd.conf instead for that very purpose. So whatever configurations residing in .htaccess-files should simply be moved to /etc/httpd.conf and said .htaccess-files removed afterwards.


[/B][/I]

---

