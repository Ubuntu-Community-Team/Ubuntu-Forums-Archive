---
title: "Xubuntu install can't find cdrom"
date: 2006-10-10
forum: Installation &amp; Upgrades
---

### Post by louieb on 2006-10-10
I am trying to install xubuntu on an old P1 200mhz w/128 mb ram. I downloaded the alternate CD and burned it. CD did install Xubuntu on an ole Emachine so I know the CD is good.
The old P1 had Ubuntu 5 installed at one time now, it is booting slackware. 
The problem with the Xubuntu install is when it gets to the point where it is looking for the installation CD it just hangs and nothing more is done. 
I've had this problem before with other distros. But a look at the documentation usally not always provides some parameter to pass at boot up time to get around this.  
I would like to replace Slack with Xubuntu.  I looked in the wiki,did a forum search for cdrom, and have tried some google searches.   Anybody know what I can try.

---

### Post by louieb on 2006-10-14
Got around the finding of CDROM by pressing the escape key and and the boot prompt entering:
```
install noapic nolapic
```

Out of curiosity I burned the CD on a different PC. But as before: it loads the kernel from the CD asks for keyboard  layout and some other stuff. Then says it is looking for the CD. It apparently finds it because it says its loading  some other stuff. The last message I get is "Starting PC card services". At that point the installation dies. 
Oh well if any other ideas pop up I'll try them. In the meantime I have reinstalled Slackware.

---

