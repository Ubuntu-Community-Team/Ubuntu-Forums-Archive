---
title: "xubuntu 13.04 libsdl1.2-dev failed to install (unmet dependencies)"
date: 2013-07-05
forum: Installation &amp; Upgrades
---

### Post by ydeweerdt on 2013-07-05
Hi,

I tried to install libsdl1.2-dev, but it fails to install with the following message.
Anybody seen the same problems?
And if so, how can I fix this?

logs see below...

Thx!

Yves

$ sudo apt-get install libsdl1.2-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 libsdl1.2-dev : Depends: libglu1-mesa-dev but it is not going to be installed or
                          libglu-dev
                 Depends: libpulse-dev but it is not going to be installed
                 Depends: libxext-dev but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


$ apt-cache policy libsdl1.2-dev libglu1-mesa-dev libglu-dev libpulse-dev libxext-dev
libsdl1.2-dev:
  Installed: (none)
  Candidate: 1.2.15-5ubuntu1
  Version table:
     1.2.15-5ubuntu1 0
        500 [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) raring/main amd64 Packages
libglu1-mesa-dev:
  Installed: (none)
  Candidate: 9.0.0-0ubuntu1
  Version table:
     9.0.0-0ubuntu1 0
        500 [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) raring/main amd64 Packages
libglu-dev:
  Installed: (none)
  Candidate: (none)
  Version table:
libpulse-dev:
  Installed: (none)
  Candidate: 1:3.0-0ubuntu6
  Version table:
     1:3.0-0ubuntu6 0
        500 [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) raring/main amd64 Packages
libxext-dev:
  Installed: (none)
  Candidate: 2:1.3.1-2
  Version table:
     2:1.3.1-2 0
        500 [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) raring/main amd64 Packages

---

### Post by slickymaster on 2013-07-05
Try it using 'aptitude' instead of 'apt-get'.

---

