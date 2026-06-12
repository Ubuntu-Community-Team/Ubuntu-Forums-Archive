---
title: "Feisty Upgrade problems (404 errors)"
date: 2007-05-07
forum: Installation &amp; Upgrades
---

### Post by Toksin on 2007-05-07
I've been trying since release to upgrade my Edgy to Feisty, but I keep getting 404 errors and then this popped up:

W: GPG error: [http://easyubuntu.cafuego.net](http://easyubuntu.cafuego.net) main Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 580E2519969F3F57


:/

I've got Feisty on a cd, but how can I upgrade using that without having to reinstall over my current installation?

---

### Post by dfreer on 2007-05-07
First, go through and comment out any repository besides the official ones ( like that easyubuntu one). Then try upgrading. If you have the feisty cd, I'm pretty sure when you insert the CD it asks if you want to upgrade or something. You could always add the cd to your /etc/apt/sources.list and upgrade as well.

---

### Post by Toksin on 2007-05-07
I get "could not download all repository indexes"

and this:

```
Failed to fetch http://packages.freecontrib.org/ubuntu/plf/dists/edgy/free/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://packages.freecontrib.org/ubuntu/plf/dists/edgy/non-free/binary-i386/Packages.gz 404 Not Found
```

How do i add the cd to the list?

---

### Post by Toksin on 2007-05-08
*bump* Anyone? :(

---

### Post by zvacet on 2007-05-08
[B]gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
gpg --export --armor KEY | sudo apt-key add -[/B]



gpg --keyserver hkp://subkeys.pgp.net --recv-keys 580E2519969F3F57
 gpg --export --armor  580E2519969F3F57  | sudo apt-key add -

---

### Post by Toksin on 2007-05-08
Nope, still getting that 404 error I posted above.

---

### Post by Topsiho on 2007-05-08
To know what a 404 error is please read:

[http://en.wikipedia.org/wiki/HTTP_404](http://en.wikipedia.org/wiki/HTTP_404)

It seems that your computer for some reason could not communicate with the server.

Topsiho

---

### Post by dfreer on 2007-05-08
> **Toksin said:**
> I get "could not download all repository indexes"

and this:

```
Failed to fetch http://packages.freecontrib.org/ubuntu/plf/dists/edgy/free/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://packages.freecontrib.org/ubuntu/plf/dists/edgy/non-free/binary-i386/Packages.gz 404 Not Found
```

How do i add the cd to the list?

Well, for one thing this repository is for edgy. get rid of all of the unofficial repositories in your /etc/apt/sources.list by placing a # in front of them. If it has archive.ubuntu.com or security.ubuntu.com it's official, EVERYTHING else is not.

Then do your update/upgrade.

To use a cd-rom repository:
[http://www.debian.org/doc/manuals/apt-howto/ch-basico.en.html#s-cdrom](http://www.debian.org/doc/manuals/apt-howto/ch-basico.en.html#s-cdrom)

EDIT:
if you get a gpg error, try typing this command into terminal:
```
gpg
```
when it gets to the part where it says "go ahead and type your message" hit ctrl-c
Then try updating again.

---

### Post by dfreer on 2007-05-08
also, when you update/upgrade use the official command:
[http://ubuntuforums.org/showthread.php?t=286599](http://ubuntuforums.org/showthread.php?t=286599)

---

### Post by Toksin on 2007-05-09
Okay, I found some repositories I'd missed.  And I'm well aware of what a 404 error is :p:)

Now I get this:

```
Error Authenticating some packages:

libpq5
```

---

### Post by dfreer on 2007-05-09
does it let you proceed, like it's a security warning? or does it muck up the upgrade?

---

### Post by Toksin on 2007-05-17
It won't let me proceed.

I tried again and it suddenly started working, but due to the fact that I'd maxed out my bandwidth, I decided to wait a few days before upgrading, once my cap switched over.

Now I get this:

```
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.bz2 MD5Sum mismatch
```

---

