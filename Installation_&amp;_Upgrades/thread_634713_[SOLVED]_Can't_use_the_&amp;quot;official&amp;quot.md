---
title: "[SOLVED] Can't use the &amp;quot;official&amp;quot; OpenOffice in Gutsy"
date: 2007-12-08
forum: Installation &amp; Upgrades
---

### Post by Irihapeti on 2007-12-08
I have uninstalled the Ubuntu version of Open Office from Gutsy and installed the version of 2.2.1 from the OpenOffice website. None of the programs will run.

When I run it in a terminal I get the following message:

```
/opt/openoffice.org2.2/program/javaldx: error while loading shared libraries: libuno_sal.so.3: cannot open shared object file: No such file or directory
/opt/openoffice.org2.2/program/soffice.bin: error while loading shared libraries: libi18nisolang1gcc3.so: cannot open shared object file: No such file or directory

```
It makes no difference which program I run, the message is the same.

I figure that I might have deleted an essential library, but all dependencies seem to be there.

Or maybe 2.2.1 doesn't work with Gutsy. Has anyone else done this and know if it works?

---

### Post by PmDematagoda on 2007-12-08
Install the following:-

```
sudo apt-get install libuno-cil
```
and

```
sudo apt-get install libi18n-java
```

Then try running Open Office.

---

### Post by Irihapeti on 2007-12-08
> **PmDematagoda said:**
> Install the following:-

```
sudo apt-get install libuno-cil
```
and

```
sudo apt-get install libi18n-java
```

Then try running Open Office.

Thanks for your interest. libuno-cil wanted to uninstall all the "official" OpenOffice files and download about 50MB of stuff I'd already removed. (Not fun on a dialup!) I gave that idea a miss.

I discovered that when I converted the RPMs with Alien in Gutsy, a number of files were left out of the .debs. I have no idea why that happened. I redid the conversion (in Feisty this time) and reinstalled in Gutsy. 

OpenOffice now works!

---

### Post by PmDematagoda on 2007-12-08
Just out of curiosity, but why are you using Open Office 2.2.1? Open Office 2.3 has already been released.

---

### Post by Irihapeti on 2007-12-08
> **PmDematagoda said:**
> Just out of curiosity, but why are you using Open Office 2.2.1? Open Office 2.3 has already been released.

Sometimes I just like to stick with a tried and true version, especially when I need it for work.

---

