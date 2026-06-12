---
title: "how do i upgrade firefox?"
date: 2010-01-31
forum: Installation &amp; Upgrades
---

### Post by blazyyo on 2010-01-31
How do I upgrade Firefox? I am using Ubuntu 8.04, and my version of Firefox is 3.0.17.

I have tried "sudo apt-get update" and "sudo apt-get upgrade" and "sudo apt-get upgrade firefox". I guess I could go to mozilla's website and download a .deb file, but is there a way to get it from the repositories? My Firefox settings are set to search for and download updates.

Please don't suggest upgrading to Ubuntu 9.10. I was using that briefly, but had gray screen freezing issues.


edit: Also I would like to download updates for all programs, including MPLayer, Kaffeine, Brasero, OpenOffice, etc. Firefox is the most important as there may be security upgrades. Thanks.

---

### Post by zvacet on 2010-02-01
You can try [Ubuntuzilla.]("http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Installation")

---

### Post by presence1960 on 2010-02-01
> **zvacet said:**
> You can try [Ubuntuzilla.]("http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Installation")

+1

You can upgrade Firefox & Thunderbird to the latest releases or any other release you desire for that matter. Once installed open a terminal and run ```
man ubuntuzilla
```
for commands to run to upgrade & other functions.

---

### Post by crichard on 2010-02-01
> How do I upgrade Firefox? I am using Ubuntu 8.04, and my version of  Firefox is 3.0.17.Download firefox from [http://mozilla.com](http://mozilla.com) and try this post about installing [Firefox / Thunderbird in Ubuntu.]("http://surferzworld.com/?p=193")

Don't miss this thread [**Firefox optimization and troubleshooting thread**]("http://ubuntuforums.org/showthread.php?t=1193567")

---

### Post by darshana on 2010-02-01
But you can use[* Synaptic* Package Manager ]("http://www.nongnu.org/synaptic/")
 its really easy.

[]("http://www.nongnu.org/synaptic/")

---

### Post by nanotube on 2010-02-01
> **presence1960 said:**
> +1

You can upgrade Firefox & Thunderbird to the latest releases or any other release you desire for that matter. Once installed open a terminal and run ```
man ubuntuzilla
```
for commands to run to upgrade & other functions.

those are old instructions, ubuntuzilla now has a repository, so there's no need to man ubuntuzilla or anything, just use the repository. :)

for latest news, see the project website, [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/)

---

### Post by nanotube on 2010-02-01
> **darshana said:**
> But you can use[* Synaptic* Package Manager ]("http://www.nongnu.org/synaptic/")
 its really easy.

[]("http://www.nongnu.org/synaptic/")

the OP says he's on hardy - synaptic won't get you a new version of firefox, unless you add a repository providing it (such as the ubuntuzilla repository)

---

### Post by presence1960 on 2010-02-01
> **nanotube said:**
> those are old instructions, ubuntuzilla now has a repository, so there's no need to man ubuntuzilla or anything, just use the repository. :)

for latest news, see the project website, [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/)

I hear you. I do have the ubuntuzilla package from the repositories installed, but I prefer to use the terminal. Once I upgraded Tbird & FF I used terminal to issue a cron command to search for updates. Either way will work.

---

### Post by Soul-Sing on 2010-02-01
> **blazyyo said:**
> How do I upgrade Firefox? I am using Ubuntu 8.04, and my version of Firefox is 3.0.17.

I have tried "sudo apt-get update" and "sudo apt-get upgrade" and "sudo apt-get upgrade firefox". I guess I could go to mozilla's website and download a .deb file, but is there a way to get it from the repositories? My Firefox settings are set to search for and download updates.

Please don't suggest upgrading to Ubuntu 9.10. I was using that briefly, but had gray screen freezing issues.


edit: Also I would like to download updates for all programs, including MPLayer, Kaffeine, Brasero, OpenOffice, etc. Firefox is the most important as there may be security upgrades. Thanks.

The best way to get the newest version of firefox is to know if your on a 64 or 32 bit system.
32 bit==>ubuntuzilla
64 bit==> add the firefox repository daily build.

---

### Post by nanotube on 2010-02-01
> **presence1960 said:**
> I hear you. I do have the ubuntuzilla package from the repositories installed, but I prefer to use the terminal. Once I upgraded Tbird & FF I used terminal to issue a cron command to search for updates. Either way will work.

that's the thing - there's no longer a need for the ubuntuzilla package, ubuntuzilla repository now directly provides packages of firefox, thunderbird, and seamonkey. 

i mean, the ubuntuzilla script still works, nothing wrong with it - but just for your information. :)

---

