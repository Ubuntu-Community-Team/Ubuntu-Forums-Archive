---
title: "problems installing opencv-2.2.0 in ubuntu 9.10"
date: 2011-02-05
forum: Installation &amp; Upgrades
---

### Post by Enthusiastic on 2011-02-05
Hi all,

  I am using opencv-2.2.0 for learning image processing
I am following the link
[http://opencv.willowgarage.com/wiki/...20%3A%20Debian]("http://opencv.willowgarage.com/wiki/InstallGuide%20%3A%20Debian")

to install this...

But even the first command to install build-essential
     Code:
     apt-get install build-essential 
is giving following errors...
     Code:
     Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  build-essential: Depends: gcc (>= 4:4.4.3) but 4:4.4.1-1ubuntu2 is to be installed
                   Depends: g++ (>= 4:4.4.3) but it is not going to be installed
                   Depends: dpkg-dev (>= 1.13.5) but it is not going to be installed
E: Broken packages 
Please help... 
Thanks in advance

Regards
Enthusiastic

---

### Post by dino99 on 2011-02-05
you should follow ubuntu links rather than third parties.

[https://launchpad.net/~gijzelaar/+archive/opencv2](https://launchpad.net/~gijzelaar/+archive/opencv2)

[http://superuser.com/questions/73859/how-to-install-opencv-in-ubuntu-karmic-koala](http://superuser.com/questions/73859/how-to-install-opencv-in-ubuntu-karmic-koala)

[http://alexsleat.co.uk/2009/12/02/howto-install-opencv-in-ubuntu-karmic-9-10/](http://alexsleat.co.uk/2009/12/02/howto-install-opencv-in-ubuntu-karmic-9-10/)

[http://jomonjohnn.blogspot.com/2010/01/how-to-install-opencv-in-ubuntu-910.html](http://jomonjohnn.blogspot.com/2010/01/how-to-install-opencv-in-ubuntu-910.html)

sidenote: remember that ubuntu is a custom debian distro, but not equal to debian (lot of ubuntu choices, differents releases and dependencies, ..., so any exotic howto is a good candidate for breakage)

---

### Post by Enthusiastic on 2011-02-05
> **dino99 said:**
> you should follow ubuntu links rather than third parties.

[https://launchpad.net/~gijzelaar/+archive/opencv2]("https://launchpad.net/%7Egijzelaar/+archive/opencv2")

[http://superuser.com/questions/73859/how-to-install-opencv-in-ubuntu-karmic-koala](http://superuser.com/questions/73859/how-to-install-opencv-in-ubuntu-karmic-koala)

[http://alexsleat.co.uk/2009/12/02/howto-install-opencv-in-ubuntu-karmic-9-10/](http://alexsleat.co.uk/2009/12/02/howto-install-opencv-in-ubuntu-karmic-9-10/)

[http://jomonjohnn.blogspot.com/2010/01/how-to-install-opencv-in-ubuntu-910.html](http://jomonjohnn.blogspot.com/2010/01/how-to-install-opencv-in-ubuntu-910.html)

sidenote: remember that ubuntu is a custom debian distro, but not equal to debian (lot of ubuntu choices, differents releases and dependencies, ..., so any exotic howto is a good candidate for breakage)

According to these links also I need to install the build-essential package and hence the same problem exist...

Please help

Regards
Enthusiastic

---

### Post by pablomun on 2011-02-05
Hi,

I've met the same problem in ubuntu 10.10 when installing build-essentials for opencv.

 [INDENT]*$ sudo apt-get install build-essential*
*Reading package lists... Done*
*Building dependency tree       *
*Reading state information... Done*
*Some packages could not be installed. This may mean that you have*
*requested an impossible situation or if you are using the unstable*
*distribution that some required packages have not yet been created*
*or been moved out of Incoming.*
*The following information may help to resolve the situation:*

*The following packages have unmet dependencies:*
* build-essential : Depends: g++ (>= 4:4.4.3) but it is not going to be installed*
*E: Broken packages*

[/INDENT]I changed the server of the repository sources to the main server instead of the local one i was using and it worked.

Regards.
Pablo.

---

### Post by dino99 on 2011-02-05
try to install from there:

[http://packages.ubuntu.com/karmic/gcc](http://packages.ubuntu.com/karmic/gcc)

[http://packages.ubuntu.com/karmic/build-essential](http://packages.ubuntu.com/karmic/build-essential)

sidenote: take care to use 32 bits package on 32 bits installation, and vice versa on 64 bits

---

