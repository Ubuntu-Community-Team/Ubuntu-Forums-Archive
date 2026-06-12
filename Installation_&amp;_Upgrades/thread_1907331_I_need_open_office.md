---
title: "I need open office"
date: 2012-01-11
forum: Installation &amp; Upgrades
---

### Post by Mariane on 2012-01-11
Hi, 

I am trying to install open office in kubuntu 11.10. I tried with rpm, as recommended by the openoffice web site and this told me to use alien instead. So I tried with alien and it didn't work. 

Instructions here:
[http://www.webupd8.org/2010/03/install-upgrade-openoffice-32-from-ppa.html](http://www.webupd8.org/2010/03/install-upgrade-openoffice-32-from-ppa.html)
are completely outdated. 

I use Antidote (advanced unfree grammar checker for French):
[http://www.druide.com/a_english.html](http://www.druide.com/a_english.html)

It says it integrates with libre office but it doesn't, it just crashes libre office. It integrates fine with open office. It adds its own menu before the "file" menu and can be lauched from within open office like open office normal spell checker. (It's actually a good idea to use both tools for French). 

Anyway, I can't get open office, I either end up with libre office or with errors. Please help.

---

### Post by Lars Noodén on 2012-01-11
Try getting it straight from the original download site:
[http://www.openoffice.org/download/other.html#tested-full](http://www.openoffice.org/download/other.html#tested-full)

Pick the appropriate .deb file and then install with [dpkg](http://manpages.ubuntu.com/manpages/oneiric/en/man1/dpkg.1.html).

---

### Post by cottfcfan on 2012-01-11
Firstly you can't install rpms in Kubuntu. Kubuntu uses debs.
You can download the deb from here:
[http://www.openoffice.org/download/other.html#tested-full](http://www.openoffice.org/download/other.html#tested-full)
Then you need to remove every trace of libreoffice:
```
sudo apt-get purge --remove libreoffice*.*
```
Then install the downloaded deb using these instructions:
[http://www.ubuntugeek.com/how-to-install-openoffice-3-2-in-ubuntu.html](http://www.ubuntugeek.com/how-to-install-openoffice-3-2-in-ubuntu.html)
Remember to change the version number and language to the on you select.

---

### Post by Mariane on 2012-01-11
Thank you

---

