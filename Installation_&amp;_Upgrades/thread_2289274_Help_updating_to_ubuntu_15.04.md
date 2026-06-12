---
title: "Help updating to ubuntu 15.04"
date: 2015-08-02
forum: Installation &amp; Upgrades
---

### Post by ryan168 on 2015-08-02
I am trying to update from ubuntu 14.04 to 15.04. I have tried using software updater, which crashes on startup, and ubuntu software center, which also crashes on startup. I have also tried running the command "apt-get dist-upgrade" in the terminal, and recieved the error: 

E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

How can I install ubuntu 15.04?

---

### Post by grahammechanical on 2015-08-02
You cannot now do what you want to do. With an LTS release (which 14.04 is) we can upgrade directly to the next LTS which will be 16.04 or change the settings to be notified of the next available release. But, the next available release would have been 14.10 and from 14.10 you could get to 15.04. But 14.10 has now reached end of life. So, there is no longer an upgrade path to 15.04.

If you have problems with 14.04 then upgrading to a newer release would not necessarily fix the problems. Unless you do a fresh install.

The command apt-get dis-upgrade does not upgrade to a newer release of Ubuntu. It upgrades the packages in the existing installation of Ubuntu. And may or may not cause breakage as there is often a reason why some packages are being held back.

Anyway, that command is not working because you are not running the command as root. "are you root?" was the question. You were not. Try it this way:

```
sudo apt-get dist-upgrade
```

But it will not upgrade to 14.10 and it may not solve any problems you may be having.

Regards.

---

### Post by lambdafox on 2015-08-02
> **grahammechanical said:**
> ...

```
sudo apt-get dist-upgrade
```

...

[COLOR=#ff0000]_***WARNING!  ***_[/COLOR]

Those are the same incomplete instructions I received before I had [this problem]("http://ubuntuforums.org/showthread.php?t=2288864").

1.  If you are using, proprietary drivers, you should completely remove them and their settings.

2.  THEN AND ONLY THEN, sudo apt-get dist-upgrade

3.  After you get logged back in, re-install your proprietary drivers

---

### Post by Vladlenin5000 on 2015-08-03
> **lambdafox said:**
> [COLOR=#ff0000]_***WARNING!  ***_[/COLOR]

Those are the same incomplete instructions I received before I had [this problem]("http://ubuntuforums.org/showthread.php?t=2288864").

1.  If you are using, proprietary drivers, you should completely remove them and their settings.

2.  THEN AND ONLY THEN, sudo apt-get dist-upgrade

3.  After you get logged back in, re-install your proprietary drivers



Actually, you're the mistaken one. Dist-upgrade, as explained before, just updates the packages already installed, eventually adding some recommended ones and has some more conflict resolution than the simple apt-get upgrade (the one you should do before dist-upgrade anyway).
The problem with proprietary drivers may occur when you upgrade the Ubuntu release, something that you should be aware by now, dist-upgrade DOESN'T do.

---

### Post by lambdafox on 2015-08-03
> **Vladlenin5000 said:**
> The problem with proprietary drivers may occur when you upgrade the Ubuntu release, something that you should be aware by now, dist-upgrade DOESN'T do.

Ah, yes, I see the difference now.  I did do-release-upgrade., not this.  The note of caution applies to that, for sure.

Based on this conversation, I think the proper way to do that is:

```
1.  Remove any proprietary drivers and their settings.
2.  sudo apt-get update
2.  sudo apt-get upgrade
4.  sudo apt-get dist-upgrade
5.  sudo do-release-upgrade
```

Is that correct?

---

