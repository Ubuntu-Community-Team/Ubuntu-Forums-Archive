---
title: "[SOLVED] Problem with perl-base"
date: 2007-12-25
forum: Installation &amp; Upgrades
---

### Post by ahawesome on 2007-12-25
I accidentally installed a new version of perl-base on Ubuntu 7.10 (perl-base 5.8.8-7ubuntu3.1). Now, I am told that I cannot install or remove any new packages, meaning I can't reinstall perl-base 5.8.8-7ubuntu3 (the version it needs). Sudo apt-get install -f only gives me an error. Is there any way I can reinstall the old version of perl-base without having to completely reinstall Gutsy? (Something I _REALLY_ don't want to do)

---

### Post by Partyboi2 on 2007-12-25
What are the error messages you are getting when you try and install/remove something?

---

### Post by ahawesome on 2007-12-26
I tried to install the package hello as an example. The text of the message the Package Installer gave me was: "Your system has broken dependencies. This application can not continue until this is fixed. To fix it, run 'sudo synaptic' or 'sudo apt-get install -f' in a terminal window." There should be a screenshot of this and the apt-get install -f results attached.

---

### Post by Partyboi2 on 2007-12-27
try
```
sudo apt-get install -f libperl5.8
```

---

### Post by ahawesome on 2007-12-27
That didn't seem to work (screenshot attached). It said libperl5.8 was already the newest version. I did sudo apt-get -f install like it said, but it was the same error message.

I also tried 'sudo apt-get install -f perl-base 5.8.8-7ubuntu3', but it said it couldn't find the package, and that perl-base was already the newest version.

---

### Post by ahawesome on 2008-01-03
Can I please get some help with this? I haven't had a reply in about a week.

---

### Post by ahawesome on 2008-01-03
Actually, I just fixed it. Downloaded the ubuntu3 version of the .deb to my home folder, went to terminal, and used the following command:

```
sudo dpkg -i perl-base_5.8.8-7ubuntu3_i386.deb
```

Fixed the package and broken dependencies. By the way, if anyone needs the package, they can find it at at [https://launchpad.net/ubuntu/gutsy/i386/perl-base/5.8.8-7ubuntu3]("https://launchpad.net/ubuntu/gutsy/i386/perl-base/5.8.8-7ubuntu3"). Make sure you download the .deb version (under file download, not source package).

---

