---
title: "Upgrading to 10.04 LTS failed - Says broken package installed"
date: 2010-08-05
forum: Installation &amp; Upgrades
---

### Post by kirtimaan on 2010-08-05
Hi,

I am trying to update OS to 10.04 LTS from 9.10 Karmic. It download some package information and then display a message while calculating size that I have some package installed which is broken and therefore upgrade can't continue. It also says that if I believe that its a bug, report with log files from /var/log/dist-upgrade/ folder.

I have checked in package manager and also used option "Fix broken pacakages" (there wasn't any reported though), but still I can't upgrade. I think I have some package installed from other repo ([http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/)) which is causing conflict. But those are display drivers and I had to install them because otherwise mono wasn't showing text on window forms. 

I have attached my apt.log and main.log file here. If any one can suggest how I can upgrade without destroying my data and keeping my apps and setting.

Thanks

---

### Post by soldier1st on 2010-08-06
well just uncheck the ppa(you won't lose it) also did you remove any default ubuntu programs?

---

