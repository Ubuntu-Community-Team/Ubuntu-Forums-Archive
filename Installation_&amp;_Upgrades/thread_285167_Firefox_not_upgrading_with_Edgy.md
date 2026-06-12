---
title: "Firefox not upgrading with Edgy"
date: 2006-10-26
forum: Installation &amp; Upgrades
---

### Post by bignickel on 2006-10-26
Hi, I just installed Edgy with

gksu "update-manager -c" 

Everything works, but it appears that firefox didn't upgrade.  It's still running at 1.5.0.3.  I can remove it and install it again, and it still loads 1.5.0.3.  Any idea what's going on?

---

### Post by bignickel on 2006-10-26
The other weird thing is that if I remove firefox using apt-get I can still run it from the command line.  Something's screwed up.

---

### Post by phrawzty on 2006-10-26
You didn't, perchance, install Firefox 1.5.x via a method *other* than apt-get, eh?  For example, i installed FF1.5x via a third-party tool called [Automatix]("http://www.getautomatix.com/"), back when FF wasn't available via the standard Ubuntu tree.  It installed FF into /opt/firefox, and made symlinks from the normal places to the installation in /opt/.

Thus, "removing" the package via apt-get didn't actually *do* anything, since only the symlinks were removed - the application was still there...

---

### Post by BarFly on 2006-10-26
> **phrawzty said:**
> You didn't, perchance, install Firefox 1.5.x via a method *other* than apt-get, eh?  For example, i installed FF1.5x via a third-party tool called [Automatix]("http://www.getautomatix.com/"), back when FF wasn't available via the standard Ubuntu tree.  It installed FF into /opt/firefox, and made symlinks from the normal places to the installation in /opt/.

Thus, "removing" the package via apt-get didn't actually *do* anything, since only the symlinks were removed - the application was still there...
I also installed via Automatix as the Ubuntu version was slower and outdated.  That was probablly back when using I had Breezy.  So, can both the poster and I d/l the tarball, extract and replace what is currentlly in /opt/firefox?  Will this cause a loss of bookmarks?

I've tried "sudo firefox" and checked for updates, but that did not work.  Should we wait untill Mozilla gets around to allowing auto updates (possiblly a week from now)?  Or, should we replace what is in /opt/firefox, or create a new directory for 2.0?

Edit:  I extracted the tarball and it seems to work fine, but I don't know where to put the files as a search reveals that FF is all over the place.

---

### Post by bignickel on 2006-10-27
Yes, that was my problem.  I don't remember installing it another way, but I guess I did at some point.  So I deleted the firefox in /usr/bin and put in a new symlink to the proper file.

---

### Post by inspired on 2006-11-04
I also have this issue.
I think I origally installed FF by downloading it manually and installing it manually back on Ubuntu 5.10).
Presently the package manager says I have Firefox 2.0 installed yet when I run firefox it is the ealier version (1.5.0.2), I guess I have the same issue as you people...FF is installed in another location.
Has anyone figured out how to resolve this issue?

---

### Post by aysiu on 2006-11-04
> **inspired said:**
> 
Has anyone figured out how to resolve this issue? Yes.

Follow [these instructions](https://help.ubuntu.com/community/FirefoxNewVersion#head-51054869b8a40ea50859b0163c806e76f882499c) to use the 2.0 packaged with Edgy.

Or, use [this script](http://pykeylogger.sourceforge.net/installnewfirefox.sh) to install 2.0 from Mozilla over the 1.5 you'd previously installed from Mozilla.

---

