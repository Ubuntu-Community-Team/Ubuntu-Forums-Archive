---
title: "Openshot installation issue 14.04"
date: 2014-05-15
forum: Installation &amp; Upgrades
---

### Post by bybgrant on 2014-05-15
Hi, I tried to install Openshot via the software centre and recieved the error 

[B]"The following packages have unmet dependencies:

openshot: Depends: python (>= 2.5) but 2.7.5-5ubuntu3 is to be installed"[/B]

so then I tried to install via a terminal window with the commands 

[B]sudo add-apt-repository ppa:openshot.developers/ppa

sudo apt-get update

sudo apt-get install openshot openshot-doc[/B]
and terminal gave the error message 

"The following packages have unmet dependencies:
 openshot : Depends: gtk2-engines-pixbuf but it is not going to be installed
E: Unable to correct problems, you have held broken packages."


I am not sure what I am doing wrong but I am new so any help much appreciated.

Grant

---

### Post by TheFu on 2014-05-15
Did you happen to install any packages directly with .deb files?

Also ... did the "update" work without errors?

I would do it this way:```

sudo aptitude update
sudo aptitude dist-upgrade
sudo aptitude install openshot
```

If issues, copy/paste **relevant** parts of the output here. That includes the exact command run.

---

