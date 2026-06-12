---
title: "Cannot install or remove on Ubuntu 9.10"
date: 2010-04-03
forum: Installation &amp; Upgrades
---

### Post by TruthDose on 2010-04-03
I get this error message; I am not able to update either. Should I do a clean install from cd? if so could someone walk me through it?


"installArchives() failed: (Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 244710 files and directories currently installed.) 
Removing xjadeo ... 
Processing triggers for desktop-file-utils ... 
Processing triggers for man-db ... 
Setting up cm-super-x11 (0.3.4-3) ... 
E: /var/lib/defoma/locked exists. 
E: Another defoma process seems running, or you aren't root. 
E: If you are root and defoma process isn't running undoubtedly, 
E: it is possible that defoma might have aborted. 
E: Please run defoma-reconfigure -f to fix its broken status. 
dpkg: error processing cm-super-x11 (--configure): 
 subprocess installed post-installation script returned error exit status 1 
Setting up ttf-sil-gentium-basic (1.1-1) ... 
E: /var/lib/defoma/locked exists. 
E: Another defoma process seems running, or you aren't root. 
E: If you are root and defoma process isn't running undoubtedly, 
E: it is possible that defoma might have aborted. 
E: Please run defoma-reconfigure -f to fix its broken status. 
dpkg: error processing ttf-sil-gentium-basic (--configure): 
 subprocess installed post-installation script returned error exit status 1 
Setting up ttf-sjfonts (2.0.2-1ubuntu1) ... 
E: /var/lib/defoma/locked exists. 
E: Another defoma process seems running, or you aren't root. 
E: If you are root and defoma process isn't running undoubtedly, 
E: it is possible that defoma might have aborted. 
E: Please run defoma-reconfigure -f to fix its broken status. 
dpkg: error processing ttf-sjfonts (--configure): 
 subprocess installed post-installation script returned error exit status 1 
Setting up ttf-tiresias (0.1-1.1) ... 
E: /var/lib/defoma/locked exists. 
E: Another defoma process seems running, or you aren't root. 
E: If you are root and defoma process isn't running undoubtedly, 
E: it is possible that defoma might have aborted. 
E: Please run defoma-reconfigure -f to fix its broken status. 
dpkg: error processing ttf-tiresias (--configure): 
 subprocess installed post-installation script returned error exit status 1 
Setting up ttf-ubuntu-title (0.3-0ubuntu1) ... 
No apport report written because MaxReports is reached already
E: /var/lib/defoma/locked exists. 
E: Another defoma process seems running, or you aren't root. 
E: If you are root and defoma process isn't running undoubtedly, 
E: it is possible that defoma might have aborted. 
E: Please run defoma-reconfigure -f to fix its broken status. 
dpkg: error processing ttf-ubuntu-title (--configure): 
 subprocess installed post-installation script returned error exit status 1 
Setting up ttf-unifont (1:5.1.20080914-1) ... 
No apport report written because MaxReports is reached already
E: /var/lib/defoma/locked exists. 
E: Another defoma process seems running, or you aren't root. 
E: If you are root and defoma process isn't running undoubtedly, 
E: it is possible that defoma might have aborted. 
E: Please run defoma-reconfigure -f to fix its broken status. 
dpkg: error processing ttf-unifont (--configure): 
 subprocess installed post-installation script returned error exit status 1 
Setting up ttf-xfree86-nonfree (4.2.1-3) ... 
No apport report written because MaxReports is reached already
E: /var/lib/defoma/locked exists. 
E: Another defoma process seems running, or you aren't root. 
E: If you are root and defoma process isn't running undoubtedly, 
E: it is possible that defoma might have aborted. 
E: Please run defoma-reconfigure -f to fix its broken status. 
dpkg: error processing ttf-xfree86-nonfree (--configure): 
 subprocess installed post-installation script returned error exit status 1 
Setting up ttf-xfree86-nonfree-syriac (4.2.1-3) ... 
No apport report written because MaxReports is reached already
E: /var/lib/defoma/locked exists. 
E: Another defoma process seems running, or you aren't root. 
E: If you are root and defoma process isn't running undoubtedly, 
E: it is possible that defoma might have aborted. 
E: Please run defoma-reconfigure -f to fix its broken status. 
dpkg: error processing ttf-xfree86-nonfree-syriac (--configure): 
 subprocess installed post-installation script returned error exit status 1 
Setting up ttf-jsmath (0.01-2) ... 
No apport report written because MaxReports is reached already
E: /var/lib/defoma/locked exists. 
E: Another defoma process seems running, or you aren't root. 
E: If you are root and defoma process isn't running undoubtedly, 
E: it is possible that defoma might have aborted. 
E: Please run defoma-reconfigure -f to fix its broken status. 
dpkg: error processing ttf-jsmath (--configure): 
 subprocess installed post-installation script returned error exit status 1 
No apport report written because MaxReports is reached already
Errors were encountered while processing: 
 cm-super-x11 
 ttf-sil-gentium-basic 
 ttf-sjfonts 
 ttf-tiresias 
 ttf-ubuntu-title 
 ttf-unifont 
 ttf-xfree86-nonfree 
 ttf-xfree86-nonfree-syriac 
 ttf-jsmath "

---

### Post by byStanderone on 2010-04-03
...try if you can untangle the mess by sudo apt-get autoclean...

---

### Post by TruthDose on 2010-04-03
nothing :/

---

### Post by coffeecat on 2010-04-03
This appears about a dozen times:

> **TruthDose said:**
> E: Please run defoma-reconfigure -f to fix its broken status. 

Did you try this from a terminal?

```
sudo defoma-reconfigure -f
```

---

