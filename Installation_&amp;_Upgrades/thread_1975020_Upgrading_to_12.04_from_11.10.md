---
title: "Upgrading to 12.04 from 11.10"
date: 2012-05-06
forum: Installation &amp; Upgrades
---

### Post by BlueSunshine on 2012-05-06
My computer has tried to upgrade numerous times to 12.04 and failed. It says I can do a "partial upgrade", but it just says:

The package system is broken

If you are using third party repositories then disable them, since they are a common source of problems.
Now run the following command in a terminal: apt-get install -f

Any help?

---

### Post by jadtech on 2012-05-06
change  the server in the update manager  would be the first thing  I  would do...
 I would do the upgrade from  the terminal window not the software update manager ..

I would also install apt python-apt if its not already installed before you start the upgrade to avoid a few of the common issues you see others posting here :) 

go to the software manager, click setting lower left hand corner ,ubuntu software tab click the download from here menu and choose a new server or US servers then close out of all click the check button and install everything listed dont click  the upgrade button even if its there  just  install any updates.. 

once that is  done and you re=boot even if it  dont tell  you too , once rebooted  go to the terminal, type these codes in order.. 

```
 sudo apt-get update
sudo apt-get install apt python-apt   

sudo apt-get do-release-upgrade


```

this should work hope it helps

---

