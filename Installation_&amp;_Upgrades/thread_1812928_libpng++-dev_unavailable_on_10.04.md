---
title: "libpng++-dev unavailable on 10.04"
date: 2011-07-27
forum: Installation &amp; Upgrades
---

### Post by Sn3akyP3t3 on 2011-07-27
I'm trying to install opencv 2.3 stable with python support as outlined in this tutorial: [http://opencv.willowgarage.com/wiki/InstallGuide%20%3A%20Debian](http://opencv.willowgarage.com/wiki/InstallGuide%20%3A%20Debian)  I realize the tutorial mentions 10.10, but I have seen other sites with mention of success with the same exact tutorial shamelessly copied and claiming to work for 10.04 and 11.04.

Among the dependencies for opencv in the tutorial is libpng++-dev which apparently is not available on 10.04, but appears to be available on other distributions.

I'm open to suggestions to get this to work.  Also, why has 10.04 omitted this in the repositories?

---

### Post by jerrrys on 2011-07-27
looks like to me, that libpng++-dev is new in 10.10.  took a look at it in synaptics and unfortunately its not just one package.  it gets into the dependency  of the dependency thing and there are also conflicts.

in my opinion, there is nothing wrong with upgrading to 10.10

edit  [http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=libpng%2B%2B&sa=Search&cof=FORID:9#921](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=libpng%2B%2B&sa=Search&cof=FORID:9#921)

---

### Post by 130s on 2011-08-01
[Sn3akyP3t3]("http://ubuntuforums.org/member.php?u=951141"),

looks like I had exactly the same problem on Ubuntu 10.04, and after upgrading to 10.10, those libraries are installed w/o errors.

# Btw, aside from the original question, OpenCV 2.3.0 might require libgtk2.0-dev once you  run a program (not for sure but I saw this runtime error on 2 different Ubuntu computers). So I install it before running CMAKE.

---

### Post by Sn3akyP3t3 on 2011-08-03
I'll take the plunge and upgrade to the latest version of Ubuntu on this machine.  I don't have any personal experience backed reasoning for sticking with the LTS releases, but I do it for my home server and at work just to avoid potential conflicts with existing installations for stability reasons.

I'm fairly certain I've already made a few mistakes on this laptop that might warrant a reinstall as a quick fix.  I need to keep proficient in recovering from disaster anyway so I'll call this a fire drill and start the timer while someone barks orders at me for simulation purposes. :)

I haven't experienced 11.04 yet so now I have an excuse.

---

