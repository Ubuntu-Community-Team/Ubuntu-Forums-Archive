---
title: "Upgrade to 11.04 from 10.10 fails"
date: 2011-10-04
forum: Installation &amp; Upgrades
---

### Post by Azrael84 on 2011-10-04
Hi, I'm having some issues upgrading from 10.10 to 11.04, the message I get is:  >  Could not calculate the upgrade  An unresolvable problem occurred while calculating the upgrade: E:Unable to correct problems, you have held broken packages.   This can be caused by:  * Upgrading to a pre-release version of Ubuntu  * Running the current pre-release version of Ubuntu  * Unofficial software packages not provided by Ubuntu  If none of this applies, then please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bug report.   Anyone know how I can fix this and perform the upgrade?   thanks

---

### Post by dino99 on 2011-10-04
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove


sudo synaptic
only use genuine ubuntu repo (desactivate the others if any) and check for broken package(s)

sudo dpkg-reconfigure -phigh -a
sudo apt-get update

---

### Post by Azrael84 on 2011-10-04
> sudo synaptic
only use genuine ubuntu repo (desactivate the others if any) and check for broken package(s) 

To do this in synaptic I just go to settings > repositories and under other software deselect  everything (spotify/ppa. etc)? I tried this an then did sudo dpkg-reconfigure -phigh -a
sudo apt-get update, but still got the same error.

Should I be doing something else? how do I check for broken packages and only use ubuntu repositories otherwise?

---

### Post by Azrael84 on 2011-10-04
I've been looking at the upgrade log:

> 2011-10-04 15:42:35,658 DEBUG Installing 'xserver-xorg-video-all' (Distro KeepInstalledPkgs rule)
2011-10-04 15:44:15,822 ERROR Dist-upgrade failed: 'E:Unable to correct problems, you have held broken packages.'
2011-10-04 15:44:15,825 DEBUG abort called 

does this mean this is what is holding things back? how do I sort this if so?

---

### Post by MAFoElffen on 2011-10-04
> **Azrael84 said:**
> I've been looking at the upgrade log:

does this mean this is what is holding things back? how do I sort this if so?
```

sudo apt-get update

```
Will refresh the update cache...

```

sudo apt-get check
 
```
Will check for broken dependencies...

```

sudo apt-get -f

```
Will try to repair any broken dependencies...
```

sudo apt-get dist-upgrade

```
Will analyze and try to resolve any unmet dependencies...

---

### Post by Azrael84 on 2011-10-07
I installed a lot of stuff and it all went through perfectly then, thanks alot.

---

