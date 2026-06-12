---
title: "cant update or install software in 6.10 (used cd from ubuntu-bible)"
date: 2008-06-07
forum: Installation &amp; Upgrades
---

### Post by cti on 2008-06-07
this is my first linux project and ive gotten myself pretty confused.

i picked up a copy of the Ubuntu Linux bible and have installed 6.1 (fiesty?) onto a sony VGN N320E laptop. i am connected to the internet via a netgear router (forget the model, a cheap one) which is hooke dup to a cable modem(hooked up to comcast cable internet) ive been attempting to update (and upgrade) ive tried through the graphical version in administration>upgrade manager and ive tried installing software in add/remove and tried using the synaptic package manager, they all give me errors (it gives me an error and tells me there something wrong with my network)

if i try

sudo apt-get update

it lets me enter password, and i get this output (or somethig similar, this is acutally copied and pasted error from using the non-command line tool, but the errors are the same, i still havent figured out hwo to copy and paste what i see in the terminal...can i re direct it to a txt file w/ |? coudltn get that to work)

[http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz:) 404 Not Found
[http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz:) 404 Not Found
[http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz:) 404 Not Found
[http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/binary-i386/Packages.gz:) 404 Not Found
[http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://us.archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://us.archive.ubuntu.com/ubuntu/dists/edgy/multiverse/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/edgy/multiverse/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.gz:) 404 Not Found
[http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/source/Sources.gz:) 404 Not Found
[http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/source/Sources.gz:) 404 Not Found
[http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/source/Sources.gz:) 404 Not Found
[http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://us.archive.ubuntu.com/ubuntu/dists/edgy/restricted/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/edgy/restricted/source/Sources.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/source/Sources.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://us.archive.ubuntu.com/ubuntu/dists/edgy/multiverse/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/edgy/multiverse/source/Sources.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/source/Sources.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/source/Sources.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/source/Sources.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/source/Sources.gz:) 404 Not Found [IP: 91.189.88.31 80]


whats going on here? how can i update my system (and move on the the even more confusing task of trying to get the wireless card to work on this pile)

i guess i shoudl mention that firefox seems to be connecting just fine, i am on the machine thats having the update problems right now

---

### Post by dstew on 2008-06-07
You have Edgy Eft, not Feisty Fawn. Edgy is not longer supported, and the Edgy updates repository has been removed, and is no longer available. I recommend you upgrade to Feisty Fawn instead. You should have that option on the Synpatic window, at the top.

You could also do the regular Hardy installation by downloading the .iso and creating a Live CD. Get it [here]("http://www.ubuntu.com/GetUbuntu/download").

---

### Post by cti on 2008-06-07
the upgrade give me the smae error. trying to conenct to anything other than firefox is giving me this same problem.

im going to try making a new live cd and see how that works.

---

### Post by cti on 2008-06-08
installing using my newly made cd worked like  charm! thanks!

---

