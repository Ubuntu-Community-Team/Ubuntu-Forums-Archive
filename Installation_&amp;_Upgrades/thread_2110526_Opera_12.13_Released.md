---
title: "Opera 12.13 Released"
date: 2013-01-30
forum: Installation &amp; Upgrades
---

### Post by shantiq on 2013-01-30
if you too like this browser it has just been updated [info courtesy of [**Liberian Geek**]("http://www.liberiangeek.net/2013/01/opera-12-13-released-install-upgrade-in-windows-mac-and-ubuntu-systems/")]


3 steps from commandline


**1.**> [noparse]wget -O- http://deb.opera.com/archive.key | sudo apt-key add -[/noparse]
[B]
2.[/B]> [noparse]sudo sh -c 'echo "deb http://deb.opera.com/opera/ stable non-free" >> /etc/apt/sources.list'[/noparse]

**3.**> sudo apt-get update && sudo apt-get install opera



> Release notes

Release date: 2013-01-30

Opera 12.13 is a recommended upgrade offering security and stability enhancements.
Fixes and Stability Enhancements since Opera 12.12
General and User Interface
Fixed an issue where Opera gets internal communication errors on Facebook
Fixed an issue where no webpages load on startup, if Opera is disconnected from the Internet
Fixed an issue where images will not load after back navigation, when a site uses the HTML5 history API (deviantart.com)
Linux and Windows
A new stand-alone update-checker, as part of a planned upgrade of the auto-update system
Windows
Improved protection against hijacking of the default search, including a one-time reset
Security
Fixed an issue where DOM events manipulation might be used to execute arbitrary code, as reported by Arthur Gerkis; see our advisory
Fixed an issue where use of SVG clipPaths could allow execution of arbitrary code, as reported by anonymous via the iSIGHT Partners GVP Program; see our advisory
Fixed a low severity security issue; details will be disclosed at a later date
 Fixed an issue where CORS requests could omit the preflight request, as reported by webpentest; see our advisory

---

### Post by Frogs Hair on 2013-01-30
You can also go to the Opera web site and download the appropriate Ubuntu .deb package and the opera stable source will be added to software sources. The browser will update automatically via the update manager.

---

### Post by vasa1 on 2013-01-30
> **Frogs Hair said:**
> You can also go to the Opera web site and download the appropriate Ubuntu .deb package and the opera stable source will be added to software sources. The browser will update automatically via the update manager.
That's what I did for 12.12 and got 12.13 a while ago the Update Manager.

---

