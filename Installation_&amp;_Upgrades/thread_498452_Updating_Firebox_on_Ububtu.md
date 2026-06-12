---
title: "Updating Firebox on Ububtu"
date: 2007-07-11
forum: Installation &amp; Upgrades
---

### Post by rpead on 2007-07-11
I"m updating Firefox with the latest version (2.0.4) on Ubunu 5.1
I've downloaded the tar.gz and placed it in the /tmp folder,but I can't choose a locale :
Please see attached eror log:
[I]
ryan@ubuntu-firewall:~$ python ~/ubuntuzilla.py -a install -p firefox -d
Your commandline options:
{'package': 'firefox', 'debug': True, 'localization': 'en-US', 'skipgpg': False, 'test': False, 'skipbackup': False, 'mirror': 'releases.mozilla.org', 'action': 'install', 'unattended': False, 'keyservers': ['subkeys.pgp.net', 'pgpkeys.mit.edu', 'pgp.mit.edu'], 'targetdir': '/opt'}
Debug mode ON.

Welcome to the Ubuntuzilla Firefox script version 4.1.1

This script installs the latest release of the official Mozilla build of Firefox on Ubuntu Linux. If you run into any problems using this script, or have feature requests, suggestions, or general comments, please visit our website at [http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla)

Apt package name: firefox
Retrieving the version of the latest release of Firefox from the Mozilla website...
The most recent release of Firefox is detected to be 2.0.0.4. Please make sure this is correct before proceeding. (You can confirm by going to [http://www.mozilla.org/](http://www.mozilla.org/))
If no version number shows, if the version shown is not the latest, or if you would like to install an older release, press 'n', and you'll be given the option to enter the version manually. Otherwise, press 'y', and proceed with installation. [y/n]?
Please enter 'y' or 'n': y
w3m: Can't load [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.4/linux-i686/](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.4/linux-i686/).
[]
w3m: Can't load [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.4/linux-i686/](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.4/linux-i686/).
Please choose the localization (language) for Firefox. Enter the number of your choice from the list below. [If you do not see a list of localizations, please check the help section of our website at [http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla) for steps you can take to resolve this problem.]

Enter your choice of localization (integer, from 0 to -1): integer, 0
Enter your choice of localization (integer, from 0 to -1): -0.4
Enter your choice of localization (integer, from 0 to -1): -0.25
Enter your choice of localization (integer, from 0 to -1): -0.3
Enter your choice of localization (integer, from 0 to -1): -1
Enter your choice of localization (integer, from 0 to -1): 1
Enter your choice of localization (integer, from 0 to -1): 2
Enter your choice of localization (integer, from 0 to -1): -0.354
Enter your choice of localization (integer, from 0 to -1): integer
Enter your choice of localization (integer, from 0 to -1): integer, -0.25
Enter your choice of localization (integer, from 0 to -1): Traceback (most recent call last):
  File "/home/ryan/ubuntuzilla.py", line 757, in ?
    bs.start()
  File "/home/ryan/ubuntuzilla.py", line 74, in start
    fi.start()
  File "/home/ryan/ubuntuzilla.py", line 97, in start
    self.install()
  File "/home/ryan/ubuntuzilla.py", line 341, in install
    while not self.getLocalizationChoice():
  File "/home/ryan/ubuntuzilla.py", line 164, in getLocalizationChoice
    self.locChoice = raw_input("Enter your choice of localization (integer, from 0 to " + str(len(self.locList) - 1) + "): ")
KeyboardInterrupt
ryan@ubuntu-firewall:~$

[/I]

Thanx

---

### Post by nanotube on 2007-07-12
well, it looks like it could be a transient network problem. i just tried releases.mozilla.org and it's up... so try running the script again and see if it works this time. please report back on how it went. :)

---

### Post by rpead on 2007-07-12
> **nanotube said:**
> well, it looks like it could be a transient network problem. i just tried releases.mozilla.org and it's up... so try running the script again and see if it works this time. please report back on how it went. :)

My point is this, should it even be going out onto the net and searching for "releases.mozilla.org" since I have already placed the tar.gz into the /tmp folder? :confused:
I've downloaded Ubuntu 7 over night, so I'll try the Firefox upgrade on the new Ubuntu version and keep everyone posted. :)

---

### Post by nanotube on 2007-07-12
> **rpead said:**
> My point is this, should it even be going out onto the net and searching for "releases.mozilla.org" since I have already placed the tar.gz into the /tmp folder? :confused:
I've downloaded Ubuntu 7 over night, so I'll try the Firefox upgrade on the new Ubuntu version and keep everyone posted. :)

well, it should, because until you choose the locale, it won't know whether the thing you placed in /tmp is the right tar.gz :)

the one thing it shouldnt be doing is not recognizing that w3m failed, and proceeding to make you choose from an empty locale list. that seems to be a problem with w3m, which still gives an exit code of 0 even when it fails. i'll fix that in the next release.

until then, just try running it again whenever, and it should work. :)

---

### Post by rpead on 2007-07-15
> **nanotube said:**
> well, it should, because until you choose the locale, it won't know whether the thing you placed in /tmp is the right tar.gz :)

the one thing it shouldnt be doing is not recognizing that w3m failed, and proceeding to make you choose from an empty locale list. that seems to be a problem with w3m, which still gives an exit code of 0 even when it fails. i'll fix that in the next release.

until then, just try running it again whenever, and it should work. :)

Erm... yeah... I agree with you 100% :o  (did that make sense to anyone?) You lost me @ the w3m part...

Anyway I'm running Feisty Fawn now and IT'S ALL GOOD.... :guitar:

---

### Post by nanotube on 2007-07-15
> **rpead said:**
> Erm... yeah... I agree with you 100% :o  (did that make sense to anyone?) You lost me @ the w3m part...

Anyway I'm running Feisty Fawn now and IT'S ALL GOOD.... :guitar:

cool. :) never mind about the w3m stuff, that was more of a note to myself as to what to get fixed. :)

---

