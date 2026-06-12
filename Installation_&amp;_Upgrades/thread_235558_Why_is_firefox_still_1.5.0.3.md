---
title: "Why is firefox still 1.5.0.3?"
date: 2006-08-13
forum: Installation &amp; Upgrades
---

### Post by realruntime on 2006-08-13
Meanwhile there is 1.5.0.6 out, but Ubuntu 6.06.1 has still 1.5.0.3

apt seems to know that 1.5.0.5 exists because apt-cache shows both versions:

```
# apt-cache showpkg firefox
Package: firefox
Versions:
1.5.dfsg+1.5.0.5-0ubuntu6.06.1(/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_main_binary-i386_Packages)(/var/lib/dpkg/status)
1.5.dfsg+1.5.0.3-0ubuntu3(/var/lib/apt/lists/at.archive.ubuntu.com_ubuntu_dists_dapper_main_binary-i386_Packages)

```
but apt-get install tells me, that I have the latest version. Which is ...0.3

Are my repositories out of date? Here my /etc/apt/sources.list:

```
deb http://at.archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb-src http://at.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb http://at.archive.ubuntu.com/ubuntu dapper universe multiverse
deb-src http://at.archive.ubuntu.com/ubuntu dapper universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse
```

---

### Post by taurus on 2006-08-13
Maybe because when Ubuntu 6.06.1 was put together, firefox 1.5.0.3 was the latest stable version and if you want to run the newer version than you are currently have, then just upgrade the bloody thing with apt-get or aptitude!!!  ](*,)

---

### Post by jordilin on 2006-08-13
I would recommend using synaptic and see what he says.

---

### Post by slakkie on 2006-08-13
i'm running 1.5.0.5 overhere (install from last thursday):
firefox    1.5.dfsg+1.5.0.5-0ubuntu6.06.1

---

### Post by realruntime on 2006-08-13
> **jordilin said:**
> I would recommend using synaptic and see what he says.

Weird. synaptic says, I have 1.5.0.5 installed. When I start firefox and go to "Help/About Firefox" it says 1.5.0.3

---

### Post by zxee on 2006-08-13
Maybe the best thing would be to just remove and re-install ff.
I have the upgrade from the alternate 6.0.6.1 disc and my ff say 1.5.0.5

---

### Post by realruntime on 2006-08-13
> **zxee said:**
> Maybe the best thing would be to just remove and re-install ff.

Thanks. Removing FF with apt-get, deleting /usr/bin/firefox, reinstalling FF and linking /usr/bin/firefox to /usr/bin/firefox.ubuntu did the trick.

---

### Post by Neobuntu on 2006-08-13
No, no, no! Let me see if I can keep this simple.

Firefox can update it's self but you use Ubuntu which takes care of ALL updates including Firefox. That's why the check updates IN FIREFOX is greyed out. 

The version thing worried me too but see, you get the Firefox version (which can ubuntu upgrade) designated best and stable for the current release of Firefox AND with the latest fixes for newer versions compiled in. 

Clarification: As I understand it, the slightly older version number; recompiled with the newer (but less tested) versions patches makes a better fit (AKA stability) into your total Ubuntu software system.

Now, I have played with installing seperate versions of Firefox and even Swiftfox via Automatix but in the end, they get left behind by the UBUNTU COMPILED FIREFOX.

Does that help? If your look at "About Firefox" you should see ubuntu and rejoice. :)

---

### Post by zxee on 2006-08-13
> **realruntime said:**
> Thanks. Removing FF with apt-get, deleting /usr/bin/firefox, reinstalling FF and linking /usr/bin/firefox to /usr/bin/firefox.ubuntu did the trick.

:) Glad that worked!

---

### Post by Neobuntu on 2006-08-17
I've also noticed Swiftfox (for your processor via Automatix ease) co-exists with Ubuntu maintained Firefox just fine. Depending on the one you start first (run one at a time), it even adjusts for all your themes and extensions. 

I suppose the plug-ins are independant and they are available for each too (via Automatix.)

Currently Swiftfox is newer but Ubuntu's Firefox updates with Ubuntu. I also seem to notice Swiftfox is now automatically upgrading itself.

You may or may not see a speed difference with Swiftfox and while it's seems stable, it's likey to have more minor glitches perhaps.

Close all windows for one before starting the other.

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.0.6) Gecko/20060803 Firefox/1.5.0.6 (Swiftfox)

---

