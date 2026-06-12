---
title: "Upgrading an old release with newer packages"
date: 2012-04-25
forum: Installation &amp; Upgrades
---

### Post by ticket on 2012-04-25
What are the problems and issues if I want to stay with an old release of Ubuntu (typically a Long Term Support release) but want to upgrade the installed packages?

Each release of Ubuntu automatically provides an upgrade of the packages, but they then remain frozen until the next release.  

So how would I go about upgrading, say, OpenShot to the latest version?
Do I need to find a .deb package?
If I install it, will it muck up my dependencies or cause future issues?

---

### Post by ajgreeny on 2012-04-25
Although it only goes some way towards what you want, I always start with a search of [www.googlubuntu.com](www.googlubuntu.com) for a ppa for any package that I want to update beyond the versions available in normal repos, eg for openshot, your own example this page is available:-
[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=openshot+ppa&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=openshot+ppa&as_qdr=all&sa=Google+Search&lang=en)
and the first entry on that is:-
[https://launchpad.net/~openshot.developers/+archive/ppa](https://launchpad.net/~openshot.developers/+archive/ppa)
which may help you with that at least.

However, the problem is not so much the packages for various applications that you want to update; it is the eventual lack of any further security updates of the many OS packages that are needed for the system to run safely.

---

### Post by snowpine on 2012-04-25
"Open Source Software" means you can always go to the website for an application (OpenShot for example), download the source code, and compile it.

The problem you will run into eventually is that the newer version of an app will have a "dependency" that your older Ubuntu release doesn't satisfy, so you have to track down and compile the dependency, and then the dependency might have dependencies of its own...

---

### Post by bcschmerker on 2012-04-25
> **snowpine said:**
> "Open Source Software" means you can always go to the website for an application (OpenShot for example), download the source code, and compile it.

The problem you will run into eventually is that the newer version of an app will have a "dependency" that your older Ubuntu release doesn't satisfy, so you have to track down and compile the dependency, and then the dependency might have dependencies of its own...Exactly the problem I'm hitting ( ](*,) ) while attempting to get several applications up to date on 10.04.4-LTS; several Packages proper for Mozilla Firefox 3.6.29 are out-of-date for Firefox 11.0, and I found that both Gecko Media Player and Moonlight have additional dependencies for upgrade to the current version (as of 25 April 2012).

---

### Post by techsupport on 2012-04-26
> **bcschmerker said:**
> Exactly the problem I'm hitting ( ](*,) ) while attempting to get several applications up to date on 10.04.4-LTS; several Packages proper for Mozilla Firefox 3.6.29 are out-of-date for Firefox 11.0, and I found that both Gecko Media Player and Moonlight have additional dependencies for upgrade to the current version (as of 25 April 2012).

Just go down the list and make sure you have all the developmental PPAs installed:

[http://debianhelp.wordpress.com/2011/12/31/to-do-list-after-installing-ubuntu-10-04-3-lucid-lts/](http://debianhelp.wordpress.com/2011/12/31/to-do-list-after-installing-ubuntu-10-04-3-lucid-lts/)

That will be about as far as you can go without upgrading to the latest version of Ubuntu.

:guitar:

---

### Post by ticket on 2012-04-26
Thanks for the feedback.
I have had bad experience with PPAs in the past (conflicts with subsequent updates from Ubuntu, and I found it was not straightforward to purge a PPA).

I'd prefer a .deb package, but if that fails, as you say, one can resort to compiling one's own binaries, which I think is safer, as you have control on how the new software gets added to your system (e.g. in usr/local/bin) and it is easy to remove.

---

### Post by snowpine on 2012-04-26
Or you could simply upgrade to 12.04, the new Long Term Support release. :)

---

