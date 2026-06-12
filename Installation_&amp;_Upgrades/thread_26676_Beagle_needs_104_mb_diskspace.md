---
title: "Beagle needs 104 mb diskspace???"
date: 2005-04-13
forum: Installation &amp; Upgrades
---

### Post by neutron on 2005-04-13
Hi!

I've followed the tutorial on the beagle site (See [http://www.beaglewiki.org/index.php/UbuntuInstall)](http://www.beaglewiki.org/index.php/UbuntuInstall)). I've modified my sources.list so I could get beagle 0.0.9 (not the cvs version). And off course I've installed mono 1.1.4. 

When I do an 'sudo apt-get install beagle' I get lot of dev packages which have to be installed: ```
Need to get 28.4MB of archives.
After unpacking 104MB of additional disk space will be used.
``` 

I'd really like to try out beagle but 104MB??? And almost every depedency is a dev package. Is there a way to avoid all those dev packages? (I'm not developing / compiling anything so it's useless to me...)

Thanks  :smile:

---

### Post by Stormy Eyes on 2005-04-13
[QUOTE=neutron]I'd really like to try out beagle but 104MB??? And almost every depedency is a dev package. Is there a way to avoid all those dev packages? (I'm not developing / compiling anything so it's useless to me...)[/QUOTE]

Since Beagle is written with Mono (a GPL implementation of Microsoft's .NET framework), there's no getting around the Mono dependencies, just as you *must* install Java if you want to use the Azureus BitTorrent client.

---

### Post by neutron on 2005-04-13
[QUOTE=Stormy Eyes]Since Beagle is written with Mono (a GPL implementation of Microsoft's .NET framework), there's no getting around the Mono dependencies, just as you *must* install Java if you want to use the Azureus BitTorrent client.[/QUOTE]

Apparently I wasn't clear. I've mono allready installed, but when I attempted to install beagle AFTER that I'd to download 24 mb, and 104mb of additional diskspace would be needed (all kind of dev files, like mozilla-dev, etc.)

I was wondering if there was a way to avoid those dev. files. Just beagle, which isn't a large package  :smile:

---

### Post by Stormy Eyes on 2005-04-13
[QUOTE=neutron]Apparently I wasn't clear. I've mono allready installed, but when I attempted to install beagle AFTER that I'd to download 24 mb, and 104mb of additional diskspace would be needed (all kind of dev files, like mozilla-dev, etc.)

I was wondering if there was a way to avoid those dev. files. Just beagle, which isn't a large package  :smile:[/QUOTE]

No, that's my fault; I was skimming. Sorry about that. I suppose you could download the beagle package and manually install it with dpkg; I think the options you want are **dpkg -fi ./beagle*.deb**, but you should refer to dpkg's man page to be sure. If that doesn't work though, then you're probably stuck installing the dev packages.

---

### Post by neutron on 2005-04-14
Thanks for your answer Stormy Eyes. I'll try that. But I can hardly believe that I'm the only one who has tried to install beagle from that repository. Come on guys, tell me how you got it working (and if you've downloaded all those dependencies or not)  :razz:

---

### Post by basse1989 on 2005-04-14
I did before I reinstalled to a clean hoary installation. It worked fine. I like beagle. :)
I installed all the packages it wanted because I just don't care. glhf :)

---

