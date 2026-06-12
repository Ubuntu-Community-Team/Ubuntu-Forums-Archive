---
title: "Upgrading to 10.04 failed"
date: 2010-05-22
forum: Installation &amp; Upgrades
---

### Post by xcrunner78 on 2010-05-22
Hello,

I went to upgrade from 9.10 to 10.04 and it wouldn't upgrade.  This is the error:

An unresolvable problem occurred while calculating the upgrade:
E:Unable to correct problems, you have held broken packages.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bug report.

I looked for the same errors on here and on the Internet and these were some solutions, but they did not work (I included the errors form the solutions)

1. I tried in the terminal to apt-get clean, sudo apt-get -f install and this is what I got: 

E: Could not open lock file /var/cache/apt/archives/lock - open (13: Permission denied)
E: Unable to lock the download directory

Any suggestions?

---

### Post by wojox on 2010-05-22
Did you use sudo for both commands?

```
sudo apt-get clean && sudo apt-get -f install
```

Do you have any other package managers open? Synaptic, Software Center...

---

### Post by alenn on 2010-05-22
get a clean install, first download ubuntu 10.04 image and then install everything from beggining.

---

### Post by kansasnoob on 2010-05-22
Close Terminal and open Synaptic. See if the "broken package" filter is of any help.

---

### Post by xcrunner78 on 2010-05-25
Got it fixed.  First, I purged my ppa with a purge-ppa package (downloaded), then using terminal got rid of the three that I had.  Rebooted, then in terminal $sudo apt-get install -f.  Then I was able to upgrade.

---

