---
title: "acroread broke my dpkg :-( (Lucid, AMD64)"
date: 2010-12-19
forum: Installation &amp; Upgrades
---

### Post by elfboi on 2010-12-19
So I had been using Adobe Reader from some launchpad repository for a while, and when I ran "sudo aptitude upgrade" about two hours ago, it just broke my dpkg and froze, I had to kill -9 it.

What happens now is this: If I run dpkg to either remove, purge, or install acroread_9.4.1-1lucid1_amd64.deb, it just freezes after giving me the following message:

elfboi@aphrodite:~$ sudo dpkg --purge --force-all acroread
dpkg: Warnung: Problem wird übergangen, weil --force angegeben ist: 
 Paket ist in einem sehr schlechten inkonsistenten Zustand - Sie sollten
 es erneut installieren, bevor Sie es zu entfernen versuchen.
(Lese Datenbank ... 632798 Dateien und Verzeichnisse sind derzeit installiert.)
Entferne acroread ...
No LSB modules are available.
nspluginwrapper: /usr/lib/nspluginwrapper/plugins/npwrapper.nppdf.so is not a valid nspluginwrapper plugin

(And then it remains frozen, needing to be killed.)
WTF?!

Now I tried the following: I used dpkg -L acroread to get a list of all the files in the package, and I removed every single one of the manually. Then I tried to dpkg --purge it again, and dkpg froze again...

What can I do to remove this bloody package? I don't really need it in the first place, except for some very few DRM'ed PDFs I get from some business partners once or twice a year.

---

### Post by elfboi on 2010-12-20
It seems that the installer/deinstaller script is running gtk-update-icon, which then uses up to 85% CPU and runs forever without terminating.

---

### Post by elfboi on 2010-12-20
After killing gtk-update-icon and running dpkg --purge --force-all acroread again, I could finally uninstall acroread. And I could also reinstall it.

---

