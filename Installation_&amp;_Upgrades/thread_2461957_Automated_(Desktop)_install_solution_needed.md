---
title: "Automated (Desktop) install solution needed"
date: 2021-05-11
forum: Installation &amp; Upgrades
---

### Post by macbreak on 2021-05-11
Hi all. 

How does one go about automating the interaction between oneself and “ubiquity”, or, more to the point, how does one automate the stuff that interaction with ubiquity, triggers, during install? I need to automate installing Ubuntu *Desktop* from within the live USB environment. 

Specifically:

* Locales and keyboard 
* WiFi password (not urgent)
* Username / password
* Where to install etc. 

Any help greatly appreciated 

I know Microsoft have solutions for Windows for “unattended” installs - I’m looking for that, but for Ubuntu. 

Thanks so much. :)

---

### Post by schragge on 2021-05-11
[UbiquityAutomation]("https://wiki.ubuntu.com/UbiquityAutomation") states
> With respect to automation, [ubiquity]("https://wiki.ubuntu.com/Ubiquity"), the desktop CD installer, works much in the same way that debian-installer, the alternate CD installer does.
See [Appendix B. Automating the installation using preseeding]("https://d-i.debian.org/manual/en.amd64/apb.html") in the *Debian Installation Guide* and [DebianInstaller/Preseed](https://wiki.debian.org/DebianInstaller/Preseed) in the Debian Wiki then.

---

### Post by ActionParsnip on 2021-05-11
personally I have a post-install script that sets up most things. If you can formulate the commands needed to setup the system you can do it this way. Another way is to have a central configuration server like chef/puppet and configure new systems that way. If you only have a small number of systems then this is quite overkill (But fun to setup).

---

### Post by TheFu on 2021-05-11
Setup a Cobbler server. That's just another option.  Automation needs vary wildly between doing it once a week and doing 500 a day.
You can also master your own release. There are Ubuntu tools for that.
There have been changes in the last year that broke some of the old methods.  If you want control over the installation completely, there are bash scripts which can be customized to do all you need based on a debian or Arch manual install methods.

---

### Post by macbreak on 2021-05-11
> **TheFu said:**
> Setup a Cobbler server. That's just another option.  Automation needs vary wildly between doing it once a week and doing 500 a day.
You can also master your own release. There are Ubuntu tools for that.
There have been changes in the last year that broke some of the old methods.  If you want control over the installation completely, there are bash scripts which can be customized to do all you need based on a debian or Arch manual install methods.

Would you mind explaining what "Cobbler" is? Many thanks.

---

### Post by ActionParsnip on 2021-05-11
[https://cobbler.github.io/](https://cobbler.github.io/)

---

### Post by TheFu on 2021-05-11
> **ActionParsnip said:**
> [https://cobbler.github.io/](https://cobbler.github.io/)

[https://help.ubuntu.com/community/Cobbler](https://help.ubuntu.com/community/Cobbler)
Alas, [https://github.com/cobbler/cobbler/issues/2339](https://github.com/cobbler/cobbler/issues/2339), so the cobbler server won't be on Ubuntu today.

But you should be able to push an ubuntu install from a RHEL Cobbler server, unless the Live-CD broke that.

---

### Post by macbreak on 2021-05-11
> **ActionParsnip said:**
> [https://cobbler.github.io/](https://cobbler.github.io/)
thanks! :)

---

