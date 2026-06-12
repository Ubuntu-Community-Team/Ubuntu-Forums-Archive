---
title: "Dependency problems after upgrade"
date: 2005-11-07
forum: Installation &amp; Upgrades
---

### Post by jalefkowit on 2005-11-07
Hi everyone...

I just upgraded my Warty to Breezy via the apt-get method described on the wiki.  It does not seem to have gone well.  The first problem was that when it was done, I couldn't start the X server -- i had to sudo apt-get dist-upgrade again from the console for everything to work.  

Now X starts up and I can log in to the GUI just fine - BUT, when I try to install or upgrade packages via Synaptic, I get the following cryptic error:

> E: postfix: subprocess post-installation script returned error exit status 1
E: mailx: dependency problems - leaving unconfigured
E: mutt: dependency problems - leaving unconfigured
E: lsb-core: dependency problems - leaving unconfigured
E: lsb-graphics: dependency problems - leaving unconfigured
E: lsb-cxx: dependency problems - leaving unconfigured
E: lsb: dependency problems - leaving unconfigured

Wha?  I'm not, as far as I know, even running Postfix....

Anybody have any ideas on how I can fix this?  Thanks!

---

### Post by jalefkowit on 2005-11-07
Never mind, I figured it out -- doing a complete uninstall of Postfix removed all the dependency problems. 

Only question now is: why did the Breezy upgrade install Postfix in the first place???

---

### Post by rajaiskandarshah on 2005-11-11
thanks.

had the same problem. uninstalling postfix worked for me as well.

---

