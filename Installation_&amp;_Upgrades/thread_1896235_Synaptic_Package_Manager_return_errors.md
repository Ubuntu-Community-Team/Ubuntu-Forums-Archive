---
title: "Synaptic Package Manager return errors"
date: 2011-12-16
forum: Installation &amp; Upgrades
---

### Post by fattyz on 2011-12-16
Hi I'm having that same problem, here is a post that details what I have been doing to no avail.

[http://raywoodcockslatest.blogspot.com/2010/07/ubuntu-1004-broken-packages-unable-to.html](http://raywoodcockslatest.blogspot.com/2010/07/ubuntu-1004-broken-packages-unable-to.html)

an example
mark@mark-laptop:~$ sudo apt-get install mplayer
[sudo] password for mark: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mplayer: Depends: libavcodec52 (>= 4:0.6-1~) but it is not going to be installed or
                    libavcodec-extra-52 (>= 4:0.6-1~) but it is not going to be installed
           Depends: libavformat52 (>= 4:0.6-1~) but it is not going to be installed or
                    libavformat-extra-52 (>= 4:0.6-1~) but it is not going to be installed
           Depends: libcaca0 (>= 0.99.beta17-1) but 0.99.beta16-3 is to be installed
           Depends: libdirectfb-1.2-9 but it is not installable
           Depends: libjack-jackd2-0 (>= 1.9.5~dfsg-14) but it is not installable or
                    libjack-0.116 but it is not installable
           Depends: libncurses5 (>= 5.7+20100313) but 5.7+20090803-2ubuntu3 is to be installed
           Depends: libx264-98 but it is not installable
E: Broken packages

ready to re install is this a bug?

---

### Post by oldos2er on 2011-12-16
Post moved to its own thread. Please don't hijack other people's threads.

---

