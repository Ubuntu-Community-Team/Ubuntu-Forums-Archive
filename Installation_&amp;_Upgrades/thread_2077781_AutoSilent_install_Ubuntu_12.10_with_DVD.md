---
title: "Auto/Silent install Ubuntu 12.10 with DVD"
date: 2012-10-29
forum: Installation &amp; Upgrades
---

### Post by hca4 on 2012-10-29
Hey :-)

I'm working on a voluntary project for street children in Honduras. I'm going this december and I'm going to install multiple laptops 50 laptop that I got donated from various companies.

I'm want to install Ubuntu on the laptops. But I want it to be as simple as possible to maintain also for people with no IT knowledge. 
What I need your guys help with is making af complete auto/silent install of Ubuntu 12.10 with base office programs (Libre office, Firefox, ...)
I want to be able to just put in a DVD in the press Enter to boot from DVD and everything else happens automatical ( Erase whole disk, Language and Keyboard option, User information etc.)

There isn't going to be installed specialized software so it's basically just a regular install that's completly automated.

I look forward to hearing from you guys.

---

### Post by dino99 on 2012-10-29
Something to start with:

[http://www.ubuntugeek.com/fully-automatic-installation-fai-non-interactive-system-to-install-customize-and-manage-ubuntu-systems.html](http://www.ubuntugeek.com/fully-automatic-installation-fai-non-interactive-system-to-install-customize-and-manage-ubuntu-systems.html)

[https://launchpad.net/~fai/+archive/ppa](https://launchpad.net/~fai/+archive/ppa)
[https://launchpad.net/~fai/+archive/testing](https://launchpad.net/~fai/+archive/testing)

---

### Post by OpenThinking on 2012-12-08
hca4, did you succeded in making an unattended installation of Ubuntu 12.10?

---

### Post by rob-bosch on 2013-11-06
Sorry I necro this old topic, but I always understood FOG was a tool to stage Windows clients. Is it possible to stage (and update) Ubuntu clients too? If so, I think I have a winner for my project.
Can anyone elaborate?

---

### Post by ian-weisser on 2013-11-06
One easy way to customize installs is to use a preseed file with the installer. See [https://help.ubuntu.com/12.04/installation-guide/i386/preseed-using.html](https://help.ubuntu.com/12.04/installation-guide/i386/preseed-using.html)

"Updates/Upgrades" is really two questions:
- Security updates can be automatic and without user interaction already (it's a setting in /etc/apt/apt.conf.d/10periodic)
- LTS to LTS updates cannot be automated. The user (or your project) must be involved once every two years. Do you expect the hardware to last that long?

You *can* mass-upgrade installs using Canonical's Landscape tool, but that's a paid service.
You can also install a project admin account on every piece of hardware, and login to the boxes to update them...but who wants hardware with a pre-installed backdoor? The image of your project may suffer.

---

### Post by oldos2er on 2013-11-06
Old thread closed. In the future please start a new thread rather than bumping an old one.

---

