---
title: "don't know how to install firefox-3.6.3.tar.bz2"
date: 2010-06-19
forum: Installation &amp; Upgrades
---

### Post by epezhman on 2010-06-19
hi , I just downloaded firefox and don't know how to install it? what are the commands? I uncompressed the tar.bz2 file but don't know how to go further , thanks

---

### Post by Chame_Wizard on 2010-06-19
That's strange,cause you can install Firefox 3.6.3  with the build in installer.

---

### Post by kmsalex on 2010-06-19
Assuming your using 10.04 then your already using 3.6.3, but the tar.bz2 doesn't come with any installer that i can remember.

If your using 9.10 do this in the terminal (go applications>accessories>terminal)

```
[INDENT]sudo add-apt-repository ppa:mozillateam/firefox-stable
[/INDENT]
``````
sudo apt-get update
 
``````
sudo apt-get install firefox-3.6
```ps: When it asks for your password you won't see anything just keep tipping and hit enter when your done.

---

### Post by kansasnoob on 2010-06-19
> **epezhman said:**
> hi , I just downloaded firefox and don't know how to install it? what are the commands? I uncompressed the tar.bz2 file but don't know how to go further , thanks

What version of Ubuntu are you using?

---

