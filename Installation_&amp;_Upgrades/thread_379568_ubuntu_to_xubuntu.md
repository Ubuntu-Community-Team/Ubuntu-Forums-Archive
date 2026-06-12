---
title: "ubuntu to xubuntu?"
date: 2007-03-08
forum: Installation &amp; Upgrades
---

### Post by rjfioravanti on 2007-03-08
I am running edgy on my laptop (ubuntu)

Is there a way I can completely switch to xubuntu without uninstalling and reinstalling from cd? 

like some way through apt?

---

### Post by taurus on 2007-03-08
```
sudo aptitude update
sudo aptitude install xubuntu-desktop
```

And if you want to remove Gnome, then use this guide.

[http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)

---

### Post by jseiser on 2007-03-28
im on a ubuntu edgy install, i just downloaded xubuntu desktop, installed, booted into the session and i when i run the commadn to remove all the ubuntu stuff from my machine i get this


"Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  openoffice.org-l10n-en-gb: Depends: openoffice.org-common (>= 2.0.4~rc3) but it is not going to be installed or
                                      language-support-en but it is not going to be installed
                             Depends: openoffice.org-common (< 2.0.5) but it is not going to be installed or
                                      language-support-en but it is not going to be installed
  openoffice.org-l10n-en-za: Depends: openoffice.org-common (>= 2.0.4~rc3) but it is not going to be installed or
                                      language-support-en but it is not going to be installed
                             Depends: openoffice.org-common (< 2.0.5) but it is not going to be installed or
                                      language-support-en but it is not going to be installed
E: Broken packages
justin@ubuntu:~$ 
"

---

