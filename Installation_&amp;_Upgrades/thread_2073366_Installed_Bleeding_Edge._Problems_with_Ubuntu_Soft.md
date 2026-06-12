---
title: "Installed Bleeding Edge. Problems with Ubuntu Software Center afterwards."
date: 2012-10-19
forum: Installation &amp; Upgrades
---

### Post by sporche on 2012-10-19
Dear All,

First time I post on the forums. I am new to Linux systems and decided to try Ubuntu. 

Last night I installed the bleeding edge pack. Unfortunately, I am facing a problem. Popus show that system packages are broken and need fix. Can't download anything through software center. 

What shows after trying -f (from what I could read on other threads):

The following packages have unmet dependencies:
 gstreamer0.10-plugins-good:i386 : Depends: libjack-jackd2-0:i386 (>= 1.9.5~dfsg-14) but it is not installed or
                                            libjack-0.116:i386
 libasound2-plugins:i386 : Depends: libjack-jackd2-0:i386 (>= 1.9.5~dfsg-14) but it is not installed or
                                    libjack-0.116:i386
 skype : Depends: lib32stdc++6 (>= 4.1.1-21) but it is not installed
         Depends: lib32asound2 (> 1.0.14) but it is not installed
 skype-bin:i386 : Breaks: skype (< 4.0.0.8-0oneiric1) but 4.0.0.7-1 is installed
E: Unmet dependencies. Try using -f.

I've used -f and ppa purge and I still can't solve this. 

Your help would be deeply appreciated.

Thanks!

:guitar:

---

### Post by Fedele on 2012-10-22
sporche,

Are you referring to this BleedingEdge? [http://sourceforge.net/projects/bleedingedge/](http://sourceforge.net/projects/bleedingedge/)

If so, I noticed that you are using Ubuntu Oneric (11.10).  I am assuming that you used 11_10_17 as it was the last release for 11.10.

What you are seeing are packages that won't install because they depend on packages that are not installable.  In the case of Skype, the package that was downloaded is outdated.  I suggest you remove those packages with the following command:

sudo apt-get remove gstreamer0.10-plugins-good libasound2-plugins:i386 skype

You may be able to get Skype installed through the Ubuntu software center on 11.10.  I don't remember.  If not, the shell script is not compiled.  Open it up and search for Skype.  If you can follow the logic, you can install the new version yourself.

The other option is to upgrade to Ubuntu 12.04, 12.10, or Mint 13.  At the moment, I have not created a 12.10 version of BleedingEdge, and I am not sure that I will, but you can get much of the software that I originally wrote the script for through the standard repositories.

Good Luck,

Fedele

---

