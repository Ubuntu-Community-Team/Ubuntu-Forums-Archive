---
title: "where are the SHA.gpg files for minimal desktop ISO install?"
date: 2015-07-08
forum: Installation &amp; Upgrades
---

### Post by greg2lapa on 2015-07-08
at releases.ubuntu.com, I can only find links to download the Ubuntu-Desktop and Ubuntu-Server editions, along with accompanying SHA256SUMS.gpg and SHA256SUMS file. I cannot find a link for the mini.iso. Why is this?

I find the mini.iso at [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD), but there is no SHA256SUMS.gpg and SHA256SUMS file (or SHA1SUMS.gpg). How do people installing the mini.iso verify the integrity and authenticate the ISO?

Will installing Ubuntu via the mini.iso essentially allow the installer to "custom build" Ubuntu with only the packages the user needs?

---

### Post by flocculant on 2015-07-08
[http://archive.ubuntu.com/ubuntu/dists/vivid/main/installer-amd64/current/images/](http://archive.ubuntu.com/ubuntu/dists/vivid/main/installer-amd64/current/images/)

For the vivid images

[http://archive.ubuntu.com/ubuntu/dists/utopic/main/installer-amd64/current/images/](http://archive.ubuntu.com/ubuntu/dists/utopic/main/installer-amd64/current/images/)

For the utopic

You can find the trusty and precise netboot images.

Never seen them on the hashes page [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

You could report it as a bug and see if they'll add the netboot hashes to that wiki page [https://launchpad.net/ubuntu/+source/ubuntu-docs/+bugs](https://launchpad.net/ubuntu/+source/ubuntu-docs/+bugs)

>  Will installing Ubuntu via the mini.iso essentially allow the installer to "custom build" Ubuntu with only the packages the user needs?  Yes.

---

### Post by ajgreeny on 2015-07-08
The md5sum and sha1sum strings are both shown for all of the mini.iso files on the page at [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD) Each string is on the actual line in the list for that .iso file.

Where did you get your .iso file from?  Did you just miss the hash strings, or did you not know how to use them?  There is a how to wiki page at [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes) with lots of links to other useful pages on the subject.

You can install the mini version and use one of the many options available to end up with a full Ubuntu OS or any of the others from the family.

I have used it recently, installed just a command line system then added lubuntu-core package and the few other packages I want, eg synaptic for package management, firefox or chromium as web-browser, abiword and gnumeric as simple office apps, gthumb for photo management, etc etc.  That way you get just what you want or need and keep it very lean and small.

---

