---
title: "HPLIP: package conflict"
date: 2012-02-08
forum: Installation &amp; Upgrades
---

### Post by Shompol on 2012-02-08
I need to install hplip from hplipopensource.com in order to use the printer.

Using Ubuntu 10.04, 32 bit. The installation script hplip-3.11.12.run bails with error message:

> Running 'sudo apt-get install --assume-yes libcups2-dev'
Please wait, this may take several minutes...
error: Package install command failed with error code 100

When trying to install libcups2-dev manually I get:

> sudo apt-get install libcups2-dev
.......
The following packages have unmet dependencies:
  libcups2-dev: Depends: libcups2 (= 1.4.3-1) but 1.4.3-1ubuntu1.3 is to be installed
                Depends: libkrb5-dev but it is not going to be installed or
                         heimdal-dev but it is not going to be installed
E: Broken packagesAny ideas?

---

### Post by Linux Dutchman on 2012-02-09
Remove all previous installed packages of HPLIP by using Synaptic. Then go to this site and follow method 2: [https://sites.google.com/site/tipsandtricksforubuntu/printer-info/hplip-driver](https://sites.google.com/site/tipsandtricksforubuntu/printer-info/hplip-driver).
 
The installation procedure will check for missing dependencies and will also remove older (previous) installed packages. In most cases this will solve the problem with HPLIP drivers.

---

### Post by Shompol on 2012-02-09
Thank you,  I will try it tonight.

---

### Post by Shompol on 2012-02-12
Ok, so i did "sudo apt-get purge hplip" and tried to reinstall - same problem
Then i purged "cups" - same problem
then i decided to go after the root of all evil and purge libcups2, which it complained about,
and it also removed packages such as libre office, gnome, compiz, etc and right now
only command line works.

Internet works and apt-get seems to function, but any attempt to reinstall gnome end in the same kind of errors: "sure we have it, but it's not going to be installed".


So I will try to reinstall OS tonight, or else my wife will make me install Windows everywhere tomorrow, including her phone and the *&^&^%&( printer!

---

### Post by Shompol on 2012-02-13
Fresh reinstall of ubuntu 10.04 32 bit (because I destroyed my system in the previous step). Installing hplip package from HP worked. It seems that it is designed to work with the original 10.04 package versions. Test page worked.

Performed full update (apt-get update), hplip still works, printed another test page. Looks like i get to keep my testicles tomorrow, although no sleep. 

Now as to how to install hplip without re-sinstalling OS:
- I found a relevant ubuntuforums thread... in French. I will post it later and maybe even see if it works.
- Will post what package versions I have now, as soon as i get some sleep.
- Hplip is a commercial distribution from HP. We can ask them to fix it.

---

