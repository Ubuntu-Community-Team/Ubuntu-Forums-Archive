---
title: "Ubuntu returns to login screen (urgent help needed)"
date: 2014-03-07
forum: Installation &amp; Upgrades
---

### Post by hojjat on 2014-03-07
This is an installation of Ubuntu 12.04 LTS with all the default programs (Unity, etc). I ran *[COLOR="#4B0082"]apt-get upgrade[/COLOR]* today, to upgrade my OS (a list of packages that were updated is below). Once the machine restarted, when I try to log in, I just keep coming back to the login screen. In the fraction of a second between the two login screens, I get a black screen which reads:

> 
* Starting CUPS printing spooler/server
* Starting crash report subission daemon
* Starting the Winbind daemon winbind
saned disabled: edit /etc/cdefault/saned


I need help to fix this problem.

I have access to TTY of course. I can also SSH into this machine, so if there is any logs you need to see to help me out, please let me know.

Here is what I have tried so far: I ran [COLOR="#4B0082"]*sudo apt-get purge nvidia-current*[/COLOR] and [COLOR="#4B0082"]*sudo apt-get install nvidia-current*[/COLOR] hoping that would fix the "saned disabled" issue, which didn't help. I also checked and realized that I don't even have an */etc/cdefault* directory on my machine. Then I found and edited the file in */etc/default/* as explained [here](http://askubuntu.com/questions/270653/why-is-saned-disabled-on-boot-ubuntu-12-04); that made the "sane disabled" error go away, but I still get kicked back to the login screen.

Here is the list of packages that were upgraded earlier today:

> 
Install: linux-image-3.2.0-60-generic:amd64 (3.2.0-60.91), linux-headers-3.2.0-60:amd64 (3.2.0-60.91), linux-headers-3.2.0-60-generic:amd64 (3.2.0-60.91)
Upgrade: tomcat6:amd64 (6.0.35-1ubuntu3.3, 6.0.35-1ubuntu3.4), libmagickcore4:amd64 (6.6.9.7-5ubuntu3.2, 6.6.9.7-5ubuntu3.3), icedtea-netx:amd64 (1.2.3-0ubuntu0.12.04.3, 1.2.3-0ubuntu0.12.04.4), libmagickwand4:amd64 (6.6.9.7-5ubuntu3.2, 6.6.9.7-5ubuntu3.3), r-base-dev:amd64 (3.0.2-1precise0, 3.0.3-1precise0), libmagickcore4-extra:amd64 (6.6.9.7-5ubuntu3.2, 6.6.9.7-5ubuntu3.3), libmagick++4:amd64 (6.6.9.7-5ubuntu3.2, 6.6.9.7-5ubuntu3.3), r-doc-html:amd64 (3.0.2-1precise0, 3.0.3-1precise0), r-recommended:amd64 (3.0.2-1precise0, 3.0.3-1precise0), xkb-data:amd64 (2.5-1ubuntu1.3, 2.5-1ubuntu1.5), icedtea-netx-common:amd64 (1.2.3-0ubuntu0.12.04.3, 1.2.3-0ubuntu0.12.04.4), icedtea-6-plugin:amd64 (1.2.3-0ubuntu0.12.04.3, 1.2.3-0ubuntu0.12.04.4), r-base-core:amd64 (3.0.2-1precise0, 3.0.3-1precise0), imagemagick-common:amd64 (6.6.9.7-5ubuntu3.2, 6.6.9.7-5ubuntu3.3), libtomcat6-java:amd64 (6.0.35-1ubuntu3.3, 6.0.35-1ubuntu3.4), linux-headers-generic:amd64 (3.2.0.59.70, 3.2.0.60.71), linux-image-generic:amd64 (3.2.0.59.70, 3.2.0.60.71), libservlet2.5-java:amd64 (6.0.35-1ubuntu3.3, 6.0.35-1ubuntu3.4), libdvdnav4:amd64 (4.2.0-1, 4.2.0-1ubuntu0.1), r-base:amd64 (3.0.2-1precise0, 3.0.3-1precise0), tomcat6-common:amd64 (6.0.35-1ubuntu3.3, 6.0.35-1ubuntu3.4), imagemagick:amd64 (6.6.9.7-5ubuntu3.2, 6.6.9.7-5ubuntu3.3), r-base-html:amd64 (3.0.2-1precise0, 3.0.3-1precise0), linux-libc-dev:amd64 (3.2.0-59.90, 3.2.0-60.91), perlmagick:amd64 (6.6.9.7-5ubuntu3.2, 6.6.9.7-5ubuntu3.3)


I also tried creating a new account and logging in with that account; same problem happened.

Any advice is highly appreciated

---

### Post by hojjat on 2014-03-07
Solved! I did more investigation, and in the lightdm logs I noticed it is complaining the ubuntu desktop session cannot be created. Then I followed [these isntrcutions](http://askubuntu.com/questions/205872/failed-to-load-session-ubuntu) and fixed it.

I still wonder how ubuntu-desktop was removed in the first place!

---

