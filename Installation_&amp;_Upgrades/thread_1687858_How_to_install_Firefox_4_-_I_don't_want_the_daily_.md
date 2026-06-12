---
title: "How to install Firefox 4 - I don't want the daily builds but I do want 64 bit version"
date: 2011-02-14
forum: Installation &amp; Upgrades
---

### Post by MountainX on 2011-02-14
The Mozilla downloads from [here]("http://www.mozilla.com/en-US/firefox/all-beta.html") do not include a 64 bit Linux version.

The only repo I have found is this one:
[http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu)

I don't want to use that repo because the daily builds quite often break Firefox and then I'm screwed until it is fixed. 

I'm looking for a 64 bit build of the latest Firefox 4.0 beta (currently 11) for Ubuntu. Anyone have a suggestion?

---

### Post by MountainX on 2011-02-16
no suggestions?

---

### Post by MountainX on 2011-04-19
SOLUTION:

To install (e.g., from "stable" repo):
------------------------------
sudo add-apt-repository ppa:mozillateam/firefox-stable
sudo apt-get update
sudo apt-get install firefox ubufox

Alternate (GUI) way to install:
-------------------------------
Go to Applications > Ubuntu Software Center from the top panel go to Edit > Software Sources and click the ‘Other Software’ tab.Press ‘Add’ button and then paste the following line
ppa:mozillateam/firefox-stable
Once the update is done you can head to System > Administration > Update Manager to perform an upgrade.

Different channels available:

Firefox-stable channel
------------------------------
completely replaces previous versions of Firefox!
ppa:mozillateam/firefox-stable


Security-testing packages
-------------------------------
halfway through the quality-assurance process.
ppa:ubuntu-mozilla-security/ppa
Report any bugs:
[https://wiki.ubuntu.com/MozillaTeam/Bugs](https://wiki.ubuntu.com/MozillaTeam/Bugs)


Daily updates
------------------------------
Under active development! Breaks periodically. Runs along side stock version (doesn't replace it)
ppa:ubuntu-mozilla-daily/ppa


Thunderbird:
-------------------------------
sudo add-apt-repository ppa:mozillateam/thunderbird-stable
sudo apt-get update
sudo apt-get upgrade

Error NOTE:
-------------------------------
The command line way will not proceed if there is an error like this:
$ sudo add-apt-repository ppa:mozillateam/firefox-stable
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error

BUT, the GUI way will proceed (after hanging a while) and the update will simply give a warning about the software being UNAUTHENTICATED. But it will install.

References:
[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)
[http://ubuntuforums.org/showthread.php?t=1712247&page=36](http://ubuntuforums.org/showthread.php?t=1712247&page=36)

---

