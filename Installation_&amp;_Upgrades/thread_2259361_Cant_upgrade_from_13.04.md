---
title: "Cant upgrade from 13.04"
date: 2015-01-03
forum: Installation &amp; Upgrades
---

### Post by lmdfarthain on 2015-01-03
I'm currently running Ubuntu 13.04. I tried obvious methods to upgrade, and other methods i've found online. None of it seems to work.
The update manager will take me to a part where it says it's downloading two files, and then it crashes. Here's the output when i rune the update-manager:
```
Checking for a new Ubuntu release
Your Ubuntu release is not supported anymore.
For upgrade information, please visit:
http://www.ubuntu.com/releaseendoflife

authenticate 'saucy.tar.gz' against 'saucy.tar.gz.gpg' 
gpg exited 2
Debug information: 


gpg: no valid OpenPGP data found.
gpg: the signature could not be verified.
Please remember that the signature file (.sig or .asc)
should be the first file given on the command line.

Traceback (most recent call last):
  File "/usr/bin/do-release-upgrade", line 152, in <module>
    fetcher.run()
  File "/usr/lib/python3/dist-packages/DistUpgrade/DistUpgradeFetcherCore.py", line 283, in run
    _("Authenticating the upgrade failed. There may be a "
  File "/usr/lib/python3/dist-packages/DistUpgrade/DistUpgradeFetcher.py", line 50, in error
    return error(self.window_main.window_main, summary, message)
AttributeError: 'NoneType' object has no attribute 'window_main'

```

Is there any way i can still upgrade or do i need to just do a fresh install?

---

### Post by schragge on 2015-01-03
You are trying to upgrade to saucy (Ubuntu 13.10), which is also no longer supported. See [uhelp]community/Upgrades#Upgrades_via_alternate_CD[/uhelp].

---

### Post by lmdfarthain on 2015-01-03
I dont know what else to do besides upgrade to saucy... I'd love to upgrade to a supported version, I just don't know how...

---

### Post by tokyobadger on 2015-01-03
What schragge is saying is that the methods you are using appear to be (from the references to saucy in your quoted output above) guiding you how to upgrade from 13.04 (raring) to 13.10 (saucy). This will no longer work as 13.10 is already end of life.

You need to find a guide for upgrading from 13.04 to at least 14.04 (probably more worthwhile than upgrading to 14.10 as it will be end of life before 14.04 which is LTS).

Is there any reason you don't want to back up your data on 13.04 and just clean reinstall 14.04?

---

### Post by grahammechanical on 2015-01-03
There is a way. Please read through this wiki page.

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

The other day, as an experiment, I installed Ubuntu 9.04 and used the information in the wiki page to upgrade to 10.04 and then to 10.10. You need to edit the sources.list file and change the URL of the server to old-releases. For example, this is one line from my present sources.list

> deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) vivid-updates main restricted

The server is gb.archive.ubuntu.com. Whatever you have has to be changed to old-releases.ubuntu.com in every line that has the server URL. To edit the sources.list file run

```
sudo -H /etc/apt/sources.list
```

do the editing, save and run

```
sudo apt-get update
sudo apt-get upgrade
```

Then open update manager and see if it warns you about using an end of life release and offers a button to start the upgrade to 13.10, which is also end of life but you should then be able to go to 14.04. You may have to edit the 13.10 sources.list file to get to 14.04. 

Regards.

---

