---
title: "Respository check or safe check?"
date: 2015-02-09
forum: Installation &amp; Upgrades
---

### Post by chihwah_li on 2015-02-09
Hello all Linux users,

I am wondering how I can check if a Ubuntu 10.04 (or for any other version) if a respository is safe or not.

For my problem with the taskbar not showing the WIFI icon and my Dropbox icon was played at the far left of the taskbar, I fixed that with:
sudo apt-add-repository ppa:gurqn/systray-trusty
sudo apt-get update
sudo apt-get upgrade

From the forum post: [http://ubuntuforums.org/showthread.php?t=2217458](http://ubuntuforums.org/showthread.php?t=2217458)

How can I know of the given PPA is safe or not? --> ppa:gurqn

Kindest regards,

Cwli

---

### Post by grahammechanical on 2015-02-09
PPAs are Personal Package Archives. Do we trust the person who wrote the code and packaged the code into an archive? That is the question.

> [COLOR=#333333][FONT=Ubuntu]PPA's do not undergo the same process of validation as packages in the main ubuntu repositories. PPA keys are cryptographically signed but are still a low security alternative to the main repository and so the user will be installing software at their own risk.

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)[FONT=inherit][/FONT][FONT=inherit][/FONT]
[/FONT][/COLOR]
Regards.

---

### Post by v3.xx on 2015-02-09
PPAs can be buggy at times.  Its best to have a way out.  Like ppa-purge or y-ppa.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=ppa+purge&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=ppa+purge&sa=Search&cof=FORID:9)

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=y+ppa+manager&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=y+ppa+manager&sa=Search&cof=FORID:9)

---

### Post by sandyd on 2015-02-09
> **chihwah_li said:**
> Hello all Linux users,

I am wondering how I can check if a Ubuntu 10.04 (or for any other version) if a respository is safe or not.

For my problem with the taskbar not showing the WIFI icon and my Dropbox icon was played at the far left of the taskbar, I fixed that with:
sudo apt-add-repository ppa:gurqn/systray-trusty
sudo apt-get update
sudo apt-get upgrade

From the forum post: [http://ubuntuforums.org/showthread.php?t=2217458](http://ubuntuforums.org/showthread.php?t=2217458)

How can I know of the given PPA is safe or not? --> ppa:gurqn

Kindest regards,

Cwli

Side Note: Ubuntu 10.04 Desktop is EOL, and the repositories are no longer maintained: [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

The ppa works by backporting the version of Unity in trusty to 10.04.

---

### Post by deadflowr on 2015-02-09
> [COLOR=#000000]How can I know of the given PPA is safe or not? --> ppa:gurqn[/COLOR]

Most ppa's, if not all listed as ppa's, are a launchpad system naming.
So go to launchpad and search for that particular users ppas.

Doing a quick one for you here's the users launchpad home page
[https://launchpad.net/~gurqn](https://launchpad.net/~gurqn)

and here's the page for the ppa for the systray-trusty packages
[https://launchpad.net/~gurqn/+archive/ubuntu/systray-trusty/+packages](https://launchpad.net/~gurqn/+archive/ubuntu/systray-trusty/+packages)
and the ppa's actual home page with the repository signing key
[https://launchpad.net/~gurqn/+archive/ubuntu/systray-trusty](https://launchpad.net/~gurqn/+archive/ubuntu/systray-trusty)
(click on the dropdown section of the add this ppa section that says "Technical details about this ppa to see the info about the keys)

From there you can go further down the rabbit hole if you wish and inspect the packages available.

PPA can be setup by absolutely anyone, so you can either
A)Investigate any ppa you want to add to your system.
B)Trust in others who have added them to their systems.
or C) Trust the ppa blindly, and let the chips fall where they may.

Hope that helps

---

