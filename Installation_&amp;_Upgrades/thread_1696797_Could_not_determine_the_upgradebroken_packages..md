---
title: "Could not determine the upgrade/broken packages."
date: 2011-02-27
forum: Installation &amp; Upgrades
---

### Post by iguanaboy on 2011-02-27
I have been upgrading 10.4 to 10.10, but in the middle of the new package download my computer turned off (outage). Now Ubuntu won't restart the upgrade or install the packages already downloaded; it tells me it "Could not determine the upgrade" and that unresolvable problems occurred, caused by held packages. How can I reset things to restart the upgrade?

---

### Post by mörgæs on 2011-03-01
It is very unfortunate to lose power during an upgrade. You will probably be better off with a clean install.

---

### Post by Sef on 2011-03-01
See if this works: System > Administration > Synaptic Package Manager > Edit > Fix Broken Packages

---

### Post by sikander3786 on 2011-03-01
If Synaptic can't fix the broken packages, we can try doing it manually from Applications > Accessories > Terminal.

Please post the complete outputs as well to let us see what is going on in there.

```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install -f
sudo dpkg --configure -a
sudo apt-get dist-upgrade
```

While posting, click the # icon in post menu and paste your text in between the generated [code] tags for readability purposes.

---

### Post by iguanaboy on 2011-03-02
Thanks! Going through sudo allowed me to upgrade to 10.10... But then I get the same "Could not determine the upgrade/broken packages" message when I try to update it. Sigh. Well, complete CD reinstall it will be then.

---

