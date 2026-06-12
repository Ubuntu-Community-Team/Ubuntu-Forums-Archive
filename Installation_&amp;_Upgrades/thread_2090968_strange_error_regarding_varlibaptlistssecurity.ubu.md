---
title: "strange error regarding /var/lib/apt/lists/security.ubuntu.com"
date: 2012-12-04
forum: Installation &amp; Upgrades
---

### Post by cetacea on 2012-12-04
I've been trying to install Catalyst Control Center for my laptop that has Radeon HD7650M. But I just keep bumping into the following error.

==========================================================

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:
E:Encountered a section with no Package: header, E: Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_quantal-security_universe_i18n_Translation-en%5fUS, E:The package lists or status file could not be parsed or opened.

==========================================================

I googled around and found some remedies that involved "sudo rm..." but that did not work, and the console said that such command was not found. What am I supposed to do? What have I done wrong? Thanks.

---

### Post by plucky on 2012-12-04
> I googled around and found some remedies that involved "sudo rm..." but that did not work, and the console said that such command was not found. What am I supposed to do? What have I done wrong? Thanks. 

It would help to see the full error report and the actual command you tried to use in the terminal window.

Copy and paste whatever the terminal is showing you.

Good Luck

---

### Post by cetacea on 2012-12-05
> **plucky said:**
> It would help to see the full error report and the actual command you tried to use in the terminal window.

Copy and paste whatever the terminal is showing you.

Good Luck

Well.. it actually is there even right after booting. I mean, there is a "stop" sign (red circle with a white bar across) next to the clock (upper right hand corner). And.. the command I used was.. I followed the instructions in this link:
[HTML]http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-ati-catalyst-video-drivers-fglrx/129200#129200[/HTML]

The second line:
```
sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev* xorg-driver-fglrx

```
gives me that same error message. 

And to be precise, the first line gave me ```
sh: 0: Can't open /usr/share/ati/fglrx-uninstall.sh

```


======

btw, the same error message keeps popping up virtually everywhere. For example, the ubuntu software center doesn't work, or rather stopped working. And the same message is found in the error report.

---

### Post by ibjsb4 on 2012-12-05
Check out the first link, post #7 and see if that will resolve one problem.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=The+package+lists+or+status+file+could+not+be+parsed+or+opened.&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=The+package+lists+or+status+file+could+not+be+parsed+or+opened.&as_qdr=all&sa=Google+Search&lang=en)

---

