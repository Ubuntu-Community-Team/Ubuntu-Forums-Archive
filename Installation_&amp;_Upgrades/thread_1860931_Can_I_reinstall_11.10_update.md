---
title: "Can I reinstall 11.10 update?"
date: 2011-10-15
forum: Installation &amp; Upgrades
---

### Post by Sirman on 2011-10-15
I am Windows user, new to Ubuntu.  My new 11.10 (update from 11.4) is running OK, but there were glitches during install, and some modules "could not install."   Let me list the glitches:

1. Dozens of "error adding" /etc/ssl/certs/ *.pem (extension files - whatever they are). 
2. "could not install" openswan-modules-dkms
    "could not install" libglade 2.0-cil
3. message with some programs : "kernel source for this kernel not installed."
    and "linux headers missing"  (Synaptic says don't install these directly from here.)
4. As with 11.4, my wireless FAILS to connect with pae kernel, DOES connect with generic.  Why?
5. I am getting frequent panic screens, when screen turns into white-on-black text, forcing me to reboot.
So, should I reinstall the update to 11.10?  a) If so, how?  b) will the update recognize that some parts were done OK and skip those parts and install only the ones that failed?
Thanks in advance.

---

### Post by raja.genupula on 2011-10-15
some times your graphics driver need update after a upgrade.
so better to boot into recovery mode and then to failsafex or low graphics mode then update your graphics drivers.

and post me the output of ```
sudo apt-get update
``` also


all the best

---

### Post by Sirman on 2011-10-15
I have no issue with graphics.

---

### Post by Sirman on 2011-10-15
How do I capture the output from the terminal, so I can post it for you.  Type exactly what I need to do. (I said I am new at this.)

---

### Post by raja.genupula on 2011-10-15
oh ok.

do this 

```
sudo apt-get update > update.txt
```

this file will be exist in your home directory.copy and paste this here or attach file to the next post.

All the best.

---

### Post by Sirman on 2011-10-16
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric InRelease
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric InRelease
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates InRelease
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release.gpg
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release.gpg
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates Release.gpg
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Sources
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted i386 Packages
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse i386 Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe Translation-en
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en_US
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Translation-en
Reading package lists...

---

### Post by raja.genupula on 2011-10-17
give me the output of ```
lsmod | grep video
```

---

### Post by Sirman on 2011-10-17
video                  18908  0

---

### Post by raja.genupula on 2011-10-17
Hi its a graphics issue too. I told you that you have graphics driver improper installation , so please install your drivers again.

All The best.

---

### Post by Sirman on 2011-10-18
You say "it" is a graphics issue.  What is a graphics issue?  The install problems I listed do not refer to problems with graphics.  I never had to install any graphics drivers, and my screen shows fine: no complaints on that front.  I thought you were trying to help me with AT LEAST 1) why my wireless does not connect with pae kernel, but does with generic, OR 2) how to rebuild the openswan and/or libglade modules that failed during installation.  Other than these, my 11.10 runs great.  I like it.  Thanks for your help.

---

