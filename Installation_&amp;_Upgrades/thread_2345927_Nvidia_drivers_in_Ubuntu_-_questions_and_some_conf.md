---
title: "Nvidia drivers in Ubuntu - questions and some confusion"
date: 2016-12-09
forum: Installation &amp; Upgrades
---

### Post by ubuntini2 on 2016-12-09
Much confusion and conflicting information in installing Nvidia drivers in Ubuntu. In my case Ubuntu-mate.

All I've learned so far is
- *don't use Nouveau!*
and
- *most problems I've encountered are due to improperly installed Nvidia drivers!*

My goal is to use my Linux workstation exclusively for GPU rendering, so installing Nvidia drivers properly is of utmost importance!

The problem with most installation guides is they act as recipes, without actually telling you WHY this is a better approach or WHY you might try an alternative.
Ok Rant over :)

A quick google search turns up the following 5 recent (within the past year) installation guides for Nvidia drivers on Ubuntu

A very simple breakdown seems to be between what I would call 'fully manual' methods using the command line (link #3 below) vs some combination of  PPA + using the Software & Updates menu.

**Question #1**
Why PPA, and in what way might this be 'better' than a fully manual install?
Link #5 below suggests PPA is untested ( so does that mean beta and possibly avoid?)

**Question #2**
If using a fully manual install (link #3) should I simply choose the most recent driver version?
The reason i ask is in link#1 (official guide?) it says that the actual version > "depends on the version of Ubuntu one is using, and what graphics card one has installed."

**Question #3**
Is it one way or the other? ie If you install your driver manually should you avoid using the Software & Updates > Other Drivers window to avoid conflicts?

**Question #4**
If unsure what driver version you have currently installed, how do you properly remove ALL installed graphics drivers to start from scratch?


1  [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia ]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")
(using Software & Updates - additional drivers method only)

2  [https://ubuntu-mate.community/t/how-to-install-graphics-card-drivers-in-ubuntu/3228](https://ubuntu-mate.community/t/how-to-install-graphics-card-drivers-in-ubuntu/3228)
(both auto using Software & Updates and manual, but no explanation as to why manual)

3 [https://linuxconfig.org/how-to-install-the-latest-nvidia-drivers-on-ubuntu-16-04-xenial-xerus](https://linuxconfig.org/how-to-install-the-latest-nvidia-drivers-on-ubuntu-16-04-xenial-xerus) 
(manual using sudo apt-get install)

4 [http://www.ubuntugeek.com/install-nvidia-367-27-drivers-in-ubuntu-16-0415-10.html](http://www.ubuntugeek.com/install-nvidia-367-27-drivers-in-ubuntu-16-0415-10.html) 
(manual using ppa +sudo apt-get install)

5 [http://www.webupd8.org/2016/06/how-to-install-latest-nvidia-drivers-in.html](http://www.webupd8.org/2016/06/how-to-install-latest-nvidia-drivers-in.html) 
(using PPA + Software & Updates window, suggests PPA is untested)

---

