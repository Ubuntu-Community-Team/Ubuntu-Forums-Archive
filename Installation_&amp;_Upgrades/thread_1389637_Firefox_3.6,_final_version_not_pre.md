---
title: "Firefox 3.6, final version not pre"
date: 2010-01-24
forum: Installation &amp; Upgrades
---

### Post by patman0623 on 2010-01-24
I would like to be able to install firefox without installing the "pre" version. I don't like running beta software for my primary browser. I already installed Namoroka, which is 3.6.1pre.

Is there a repository I can add for this? I will already have to remove one of my repositories and remove firefox.

---

### Post by Mixalis0 on 2010-01-25
Try Ubuntuzilla; it's a nice python script that should keep your Firefox up-to-date.

See installation instructions here:
[http://techdrivein.blogspot.com/2010/01/install-firefox-36-in-ubuntu-super-easy.html](http://techdrivein.blogspot.com/2010/01/install-firefox-36-in-ubuntu-super-easy.html)

---

### Post by nanotube on 2010-01-25
indeed, try ubuntuzilla - but not the instructions Mixalis0 posted. those are outdated - ubuntuzilla is now a repository, not a python script.

get the latest straight from the source:
[http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/)

---

### Post by patman0623 on 2010-01-25
> **nanotube said:**
> indeed, try ubuntuzilla - but not the instructions Mixalis0 posted. those are outdated - ubuntuzilla is now a repository, not a python script.

get the latest straight from the source:
[http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/)*Until such a time as Mozilla decides to release 64bit builds, this repository will only host 32bit packages. *

No one bothers to compile the stable Mozilla build for 64-bit?

---

### Post by aysiu on 2010-01-25
> **Mixalis0 said:**
> Try Ubuntuzilla; it's a nice python script that should keep your Firefox up-to-date.

See installation instructions here:
[http://techdrivein.blogspot.com/2010/01/install-firefox-36-in-ubuntu-super-easy.html](http://techdrivein.blogspot.com/2010/01/install-firefox-36-in-ubuntu-super-easy.html)
I think those instructions are outdated.

There are a couple of commands to paste into the terminal to add the UbuntuZilla repositories, but after that you don't need to invoke the terminal to install Firefox. It shows up in Synaptic as *firefox-mozilla-build*

---

### Post by nanotube on 2010-01-25
> **patman0623 said:**
> *Until such a time as Mozilla decides to release 64bit builds, this repository will only host 32bit packages. *

No one bothers to compile the stable Mozilla build for 64-bit?

well, at least mozilla doesn't.

you can get the daily builds from the daily repository, which includes 64bit, but you say you want stable...

there's a new 'firefox-stable' ppa on launchpad, maybe that'll do it for you, give it a try:
[https://launchpad.net/~mozillateam/+archive/firefox-stable/](https://launchpad.net/~mozillateam/+archive/firefox-stable/)

---

### Post by patman0623 on 2010-01-25
> **nanotube said:**
> there's a new 'firefox-stable' ppa on launchpad, maybe that'll do it for you, give it a try:
[https://launchpad.net/~mozillateam/+archive/firefox-stable/](https://launchpad.net/~mozillateam/+archive/firefox-stable/)there, that did it, thanks!

---

### Post by crichard on 2010-01-29
> **patman0623 said:**
> I would like to be able to install firefox without installing the "pre" version. I don't like running beta software for my primary browser. 

It's highly recommended to install firefox from [http://mozilla.com](http://mozilla.com)

Have a look at this post to install [Firefox / Thunderbird in Ubuntu.]("http://surferzworld.com/?p=193")

---

### Post by extremizt on 2010-02-03
Guys, I am a huge fan of Ubuntuzilla, since I first installed Firefox 3.5 using it. Now with Ubuntuzilla repository, it has become even more easier. I strongly recommend Ubuntuzilla instead of other means, not just for Firefox 3.6, but for future releases too.

Here is the post on Ubuntuzilla repository.
[http://techdrivein.blogspot.com/2010/02/ubuntuzilla-repository-makes-firefox-36.html]("http://techdrivein.blogspot.com/2010/02/ubuntuzilla-repository-makes-firefox-36.html")

---

### Post by patman0623 on 2010-02-03
Again, Ubuntuzilla is not an option for 64 bit users.

---

