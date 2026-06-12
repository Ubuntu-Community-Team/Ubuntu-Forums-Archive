---
title: "Amuled"
date: 2005-05-24
forum: Installation &amp; Upgrades
---

### Post by sciurus on 2005-05-24
Here's how I successfully compiled the daemon and webcontrols for [Amule](http://www.amule.org/) 

1)
sudo apt-get install build-essential
sudo apt-get install zlib1g-dev
sudo apt-get install libpng12-dev
sudo apt-get install gettext
sudo apt-get install libwxgtk2.5-dev
#Note: Universe must be enabled to install libwxgtk2.5-dev


3)
wget [http://kent.dl.sourceforge.net/sourceforge/amule/aMule-2.0.1.tar.bz2](http://kent.dl.sourceforge.net/sourceforge/amule/aMule-2.0.1.tar.bz2)
bzip2 -d aMule-2.0.1.tar.bz2
tar -xf aMule-2.0.1.tar
cd aMule-2.0.1
./configure --enable-amulecmd --enable-webserver --disable-monolithic --enable-amule-daemon
make
sudo make install

4)
amuled
follow directions at [http://www.amule.org/wiki/index.php/Webserver#Webserver_with_aMule_2.0.0_or_later](http://www.amule.org/wiki/index.php/Webserver#Webserver_with_aMule_2.0.0_or_later)

---

### Post by Endolith on 2009-03-16
Any updated directions for this?  There's a script in /etc/init.d/amule-daemon, but trying to run it says:

```
 * Not starting aMule daemon, AMULED_USER not set in /etc/default/amule-daemon.
```Of course this file does not exist, and the only instructions I can find are less than helpful:
> 
open  /etc/default/amule-daemon
Make it run.> Configure the daemon 
    * Edit /etc/default/amule-daemon
   * /etc/init.d/amule-daemon start


---

### Post by bapoumba on 2009-03-18
Are you aware this is a 2005 thread ? ;)
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=461774](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=461774)
[https://bugs.launchpad.net/ubuntu/+source/amule/+bug/260471](https://bugs.launchpad.net/ubuntu/+source/amule/+bug/260471)

Looks fixed in Jaunty, if this is the correct error (just googled it, sorry, I cannot test).

---

### Post by Endolith on 2009-03-18
> **bapoumba said:**
> Are you aware this is a 2005 thread ? ;)

Yes.  It seems that any information about this online is out-of-date.  Anyone know of instructions that work for the current version?

---

### Post by bapoumba on 2009-03-18
Okay. Good luck and cheers.

---

### Post by Endolith on 2009-03-18
I guess "[Packaging and Compiling Programs]("http://ubuntuforums.org/forumdisplay.php?f=44")" is not a good place to ask this, though.  Sorry for resurrecting in a dumb place.

---

### Post by bapoumba on 2009-03-18
Moved to Installation & Upgrades, then :KS

---

