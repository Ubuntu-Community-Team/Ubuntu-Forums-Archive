---
title: "No firefox after update to 22.04"
date: 2022-08-31
forum: Installation &amp; Upgrades
---

### Post by triplemaya on 2022-08-31
Update leaves me with no firefox. 

running Ubuntu MATE

A long time ago I may have disabled snap on advice online because firefox was running slow. 

THE PROBLEM

sudo apt install firefox

The following packages have unmet dependencies.
 firefox : PreDepends: snapd but it is not installable
E: Unable to correct problems, you have held broken packages.

$ apt-mark showhold
NOTHING

sudo apt install snap
snap is already the newest version (2013-11-29-11).

i google:
firefox : PreDepends: snapd but it is not installable

insturctions
Remove the currently-installed version of Firefox
sudo apt remove sudo apt update 

Package 'firefox' is not installed, so not removed

sudo apt update 

sudo apt install firefox
 firefox : PreDepends: snapd but it is not installable

SO 

NO PROGRESS

i GOOGLE 
UBUNTU BROKEN PACKAGES

follow instructions:

sudo apt update --fix-missing

2 packages can be upgraded. Run 'apt list --upgradable' to see them.
W: [https://packagecloud.io/slacktechnologies/slack/debian/dists/jessie/InRelease:](https://packagecloud.io/slacktechnologies/slack/debian/dists/jessie/InRelease:) Key is stored in legacy trusted.gpg keyring (/etc/apt/trusted.gpg), see the DEPRECATION section in apt-key(8) for details.

$ apt list --upgradable
Listing... Done
firefox-locale-en/jammy,jammy 1:1snap1-0ubuntu2 amd64 [upgradable from: 104.0+build3-0ubuntu0.20.04.1]
thermald/jammy-updates 2.4.9-1ubuntu0.1 amd64 [upgradable from: 2.4.9-1]

I TRY:

sudo apt upgrade
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  firefox-locale-en thermald
0 to upgrade, 0 to newly install, 0 to remove and 2 not to upgrade.

I AM STUMPED

i GOOGLE   firefox-locale-en thermald
BUT I DO NOT GET ANYTHING i UNDERSTRAND

I GO BACK TO PRVIOUS INSTRUCTIONS
NEXT IS:
Force APT to Correct Missing Dependencies or Broken Packages

sudo apt install -f
0 to upgrade, 0 to newly install, 0 to remove and 2 not to upgrade.

SO NO CHANGE THERE

NEXT WE TRY:

Force Reconfigure or Remove Broken Packages with DPKG

sudo dpkg --configure -a
NOTHING

FINAL SUGGESTOIN ON THOSE INSTRUCTIONS

Resolve DPKG Lock Issue
sudo rm /var/lib/apt/lists/lock

NOTHING

---

### Post by triplemaya on 2022-08-31
I have downloaded firefox and can run it from the source [WHY did I not just do this before?!]

I would still appreciate a bit of support in fixing whatever is wrong with my system. :)

---

### Post by &amp;KyT$0P# on 2022-08-31
In what way is this broken for you?  Are you trying to install snapd?  Or are you trying to update Firefox while **_not_** installing the snap package of Firefox?

In either case, please post the output from running this command in Terminal -
```
for i in /etc/apt/preferences.d/*;do echo " -- $i --";cat "$i";done
```

---

### Post by vanadium on 2022-08-31
It sounds as if you disabled snap. The upgrade will remove the `.deb` version of firefox, but will not be allowed to install the snap version. So that leaves you without Firefox. If you do not want snap, you can nowadays connect to a PPA of Mozilla for a .deb installation of the browser.

---

### Post by ajgreeny on 2022-08-31
The package **snap** that you tried to install, only to be told that it was already the latest version, has nothing to do with the snap package system but is related to DNA genes, probably not something you needed at all.

Quoted from synaptic:
> SNAP is a general purpose gene finding program suitable for both eukaryotic
and prokaryotic genomes. SNAP is an acroynm for Semi-HMM-based Nucleic Acid
Parser.
What you need for snap packages is **snapd** as already mentioned by halogen2.

If the directly downloaded tar.gz version of firefox works for you as it does for me (I have removed the complete snap infrastructure from my system) use it and don't even think your system is broken; it's not!

---

### Post by triplemaya on 2022-08-31
~$ for i in /etc/apt/preferences.d/*;do echo " -- $i --";cat "$i";done
 -- /etc/apt/preferences.d/pin-xalt7x-chromium-deb-vaapi --
Package: *
Pin: release o=LP-PPA-xalt7x-chromium-deb-vaapi
Pin-Priority: 1337
 -- /etc/apt/preferences.d/snapd --
Package: snapd
Pin: origin *
Pin-Priority: -1
 -- /etc/apt/preferences.d/syncthing --
Package: *
Pin: origin apt.syncthing.net
Pin-Priority: 990

---

### Post by triplemaya on 2022-08-31
Hi. Thanks. Output posted.

I decided to give up on trying to do without snap. (I'm hoping it will get better because it certainly seemed to be causing problems.) So I just want it all to work with standard updates and upgrades, which I assume means using snapd.

---

### Post by triplemaya on 2022-08-31
Hi. Thanks. Good grief! Surely the authors could have come up with a more distinctive name than snap. GnUsnap perhaps!

So, while the directly downloaded tar.gz version of firefox works for me, the rest of the system seems a bit iffy. And I am thinking perhaps that is to do with snapd not working. In open office the search box is not working properly. Plus I would have to reset the open with in thunderbird because now it opens web pages with Konquerer. And I have a thought the one thing after another may surface. So just aiming for a standard system which will update and upgrade without problems.

---

### Post by &amp;KyT$0P# on 2022-08-31
The problem you're hitting is that apt is trying to install whatever is the highest version "firefox" package, which is the installer for the snap package of Firefox, but it can't because you've blocked snapd.  So it kept part of your old Firefox .deb installation from 20.04 repositories.

Just continue using the tar.bz2 Firefox direct from Mozilla, and do this to fix apt -
```
sudo apt-get purge 'firefox*'
```

No need to give up on blocking snapd.

---

### Post by oldfred on 2022-08-31
If you want the .deb version from the ppa, not the snap version, you also must reset priorities. Or it will keep trying to install the snap version.
Best to use ppa, rather than downloading .deb.

Details:
Remove snap Firefox & use ppa
[https://www.kubuntuforums.net/forum/general/documentation/how-to-s/662503-how-to-set-priority-for-a-ppa-i-e-using-firefox-without-snapd](https://www.kubuntuforums.net/forum/general/documentation/how-to-s/662503-how-to-set-priority-for-a-ppa-i-e-using-firefox-without-snapd)
[https://fostips.com/ubuntu-21-10-two-firefox-remove-snap/](https://fostips.com/ubuntu-21-10-two-firefox-remove-snap/)
[https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04](https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04)

---

### Post by triplemaya on 2022-09-01
Thanks. But I decided to give up on trying to do without snap. So I would be grateful for help in getting it all to work with snap so that future updates are not problematic.

---

### Post by vanadium on 2022-09-02
Either reinstall snap and install firefox, or install a .deb version instead. Nowadays, Mozilla maintains a version of the regular release for Ubuntu in their PPA. There are several guides on how to install the Mozilla .deb version, including [this one](https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04) on OMGUbuntu.

---

