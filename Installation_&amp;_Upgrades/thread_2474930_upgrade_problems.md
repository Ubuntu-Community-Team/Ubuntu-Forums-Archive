---
title: "upgrade problems"
date: 2022-05-11
forum: Installation &amp; Upgrades
---

### Post by grahaml2 on 2022-05-11
Every time i try to upgrade to the latest version of Ubuntu i get the below message, other than downloading the os and creating a usb install is there a way to just upgrade

W:Updating from such a repository can't be done securely, and is therefore disabled by default., W:See apt-secure(8) manpage for repository creation and user configuration details., E:The repository 'http://gb.archive.ubuntu.com/ubuntu disco-updates Release' does not have a Release file., W:Updating from such a repository can't be done securely, and is therefore disabled by default., W:See apt-secure(8) manpage for repository creation and user configuration details., E:The repository 'http://gb.archive.ubuntu.com/ubuntu disco-backports Release' does not have a Release file., W:Updating from such a repository can't be done securely, and is therefore disabled by default., W:See apt-secure(8) manpage for repository creation and user configuration details., E:The repository 'http://security.ubuntu.com/ubuntu disco-security Release' does not have a Release file.

---

### Post by ajgreeny on 2022-05-11
Which version are you trying to update from?
The version disco 19.04 has been gone from repos for a long time now; it was not an LTS version so had a left of 9 months only, ie, until Jan 2020.

You will have to clean install following a backup of all your personal files.

---

### Post by guiverc on 2022-05-11
Ubuntu 19.04 is END OF LIFE  - [http://fridge.ubuntu.com/2020/01/23/ubuntu-19-04-disco-dingo-end-of-life-reached-on-january-23-2020/](http://fridge.ubuntu.com/2020/01/23/ubuntu-19-04-disco-dingo-end-of-life-reached-on-january-23-2020/)

Key is in your pastes the codename of the release is *disco*; short for *disco dingo* or Ubuntu 19.04.

It upgraded to Ubuntu 19.10  (the 2019-October release) and the upgrade path was *gone* the moment 19.10 reached EOL - [http://fridge.ubuntu.com/2019/07/19/ubuntu-18-10-cosmic-cuttlefish-end-of-life-reached-on-july-18-2019/](http://fridge.ubuntu.com/2019/07/19/ubuntu-18-10-cosmic-cuttlefish-end-of-life-reached-on-july-18-2019/)

Ubuntu LTS releases have two upgrade paths; (1) to the next release, or (2) to the next LTS release. Your use of a non-LTS meant you were limited to the next release only.

If your machine was *i386*, as *disco* was the last fully-supported release, you cannot advance any further.  A re-install of a prior 18.04 LTS system being the only suitable option, if your machine is a different architecture, re-installing a later *supported* release is your best bet, and stick to LTS releases if you don't like *release-upgrading* every 6-9 months as required by non-LTS releases like Ubuntu 19.04.

To ensure your system is fully upgraded, the following maybe helpful - [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

Also remember, 19.04 tells you it was the 2019-April release (a *year.month* format is used by releases)thus calculating it's EOL which is nine-months after release; is pretty easy - January 2020, even if you don't read the upgrade notice on your system (*which will appear once, and if you tell it not to appear again it doesn't!*)

FYI:  You can *upgrade via re-install* desktop systems, but you didn't specify if you're using a server or desktop system, and what packages (esp. 3rd party) are involved. It works best if you're not using 3rd party packages. You just install the release you want, re-using existing partitions **without format **(it's this which triggers the install type)... There can be complications depending on when/how you installed though  (eg. *if using a no-longer used encryption; later media won't have the packages available so you need to add them prior to starting the installer etc*).

---

### Post by grahaml2 on 2022-05-12
My os version is 21.10 which i believe is an interim or EOL release, its probable that being on this version is whats giving me an upgrade to LTS problem. Upgrading to LTS would be ok.
  				 					guiverc gave a number of links, the EOLUgrades looks useful but i'm not sure which bits i'd need to do or not do - more help would be appreciated.
Thanks to all who replied

---

### Post by guiverc on 2022-05-12
> **grahaml2 said:**
> 
```
E:The repository 'http://gb.archive.ubuntu.com/ubuntu disco-updates Release' does not have a Release file.
E:The repository 'http://gb.archive.ubuntu.com/ubuntu disco-backports Release' does not have a Release file.
E:The repository 'http://security.ubuntu.com/ubuntu disco-security Release' does not have a Release file.
```


Ubuntu 19.04 was *disco dingo*, where as Ubuntu 21.10 is *impish indri*.

Your paste shows sources for Ubuntu 19.04, meaning they either don't belong, and someone with `sudo` rights has made mistakes, or you're not using Ubuntu 21.10 which would have *impish* listed on those lines instead of *disco*.

---

### Post by Impavidus on 2022-05-12
Either you somehow got disco sources in your /etc/apt/sources.list of a non-disco system, in which case you have to clean that file, or you're on disco, in which case you need either a fresh install or an upgrade by reinstall.

Could you show us the contents of your /etc/atp/sources.list?

21.10 is an interim release, but not yet at end of life. I'm still using it.

---

### Post by grahaml2 on 2022-05-12
the contents of etc/atp/sources.list
If i have to alter anything in this list how do i do it - i believe its protected ??

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://mirrors.ukfast.co.uk/sites/archive.ubuntu.com/](http://mirrors.ukfast.co.uk/sites/archive.ubuntu.com/) impish main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://mirrors.ukfast.co.uk/sites/archive.ubuntu.com/](http://mirrors.ukfast.co.uk/sites/archive.ubuntu.com/) impish-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://mirrors.ukfast.co.uk/sites/archive.ubuntu.com/](http://mirrors.ukfast.co.uk/sites/archive.ubuntu.com/) impish universe
deb [http://mirrors.ukfast.co.uk/sites/archive.ubuntu.com/](http://mirrors.ukfast.co.uk/sites/archive.ubuntu.com/) impish-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) disco-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://mirrors.ukfast.co.uk/sites/archive.ubuntu.com/](http://mirrors.ukfast.co.uk/sites/archive.ubuntu.com/) impish multiverse
deb [http://mirrors.ukfast.co.uk/sites/archive.ubuntu.com/](http://mirrors.ukfast.co.uk/sites/archive.ubuntu.com/) impish-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://mirrors.ukfast.co.uk/sites/archive.ubuntu.com/](http://mirrors.ukfast.co.uk/sites/archive.ubuntu.com/) impish-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) disco-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) disco partner

deb [http://mirrors.ukfast.co.uk/sites/archive.ubuntu.com/](http://mirrors.ukfast.co.uk/sites/archive.ubuntu.com/) impish-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) disco-security main restricted
deb [http://mirrors.ukfast.co.uk/sites/archive.ubuntu.com/](http://mirrors.ukfast.co.uk/sites/archive.ubuntu.com/) impish-security universe
deb [http://mirrors.ukfast.co.uk/sites/archive.ubuntu.com/](http://mirrors.ukfast.co.uk/sites/archive.ubuntu.com/) impish-security multiverse

# This system was installed using small removable media
# (e.g. netinst, live or single CD). The matching "deb cdrom"
# entries were disabled at the end of the installation process.
# For information about how to configure apt package sources,
# see the sources.list(5) manual.

---

### Post by Impavidus on 2022-05-13
You can edit the file with```
sudoedit /etc/apt/sources.list
```
That's the safe and secure way to edit files with root permission. It will ask for your password and open a text editor to edit the file. Unless you configured it otherwise, it will use the nano text editor. Use arrow keys no navigate, ctrl+o to save and ctrl+x to close.

There are a few lines containing the phrase disco. Change that to impish. Most of those lines refer to source repositories. You don't really need them, unless you want to look at source code, so you could disable them by prepending a #. One is the partner repository. It's no longer used, so you can disable that one too.

You run Ubuntu 21.10, but the disabled entries in sources.list were not updated when upgrading from disco to impish and gave an error when enabled on impish.

---

### Post by grahaml2 on 2022-05-13
impavidus
Thanks that worked am now updated to 22.04 LTS
I now have a little more knowledge

And you know what they say 'A little more knowledge is a little more dangerous'

---

