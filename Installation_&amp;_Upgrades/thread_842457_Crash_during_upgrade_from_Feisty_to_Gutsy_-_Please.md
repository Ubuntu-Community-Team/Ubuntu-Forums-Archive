---
title: "Crash during upgrade from Feisty to Gutsy - Please help"
date: 2008-06-27
forum: Installation &amp; Upgrades
---

### Post by Grizzlitiger on 2008-06-27
Hi,

I tried to upgrade from Feisty to Gutsy (7.04 to 7.10) but during the upgrade my laptop crashed. 
I then tried to restart the laptop and start the upgrade again but it wouldn't let me get into the graphical (Gnome) interface. I then tried to boot via the recovery mode (ie no graphical) interface and then to restart the upgrade, but instead of starting the upgrade it gave me the error message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.

so I ran 'dpkg --configure -a' which then crashed dpkg with an error message that can't recall. :confused:

So basically I want to upgrade the system now if possible using a livecd or otherwise because I don't want to make a fresh install.

Thanks for any help!:)

---

### Post by Kevbert on 2008-06-27
The message suggests you've unpacked a package but haven't configured it yet.
It may be worth trying
```
sudo apt-get install -f
```
to repair any damaged packages.

---

### Post by Grizzlitiger on 2008-06-28
Hi there,

thanks a lot for your help. I had already started trying something different which did work out in the end so I couldn't try your idea out - sorry about that!
Information for everyone else with similar problems:
The way I resolved it was by downloading and burning the alternative CD for Ubuntu 7.10 and choosing the option "Rescue a broken system" on bootup. After answering some questions you can choose to get a shell which you can use to rescue the system. I first tried to do "sudo apt-get upgrade" but then it gave me the same error message for dpkg again, so I ran "dpkg --configure -a" again and after about 2 hours and some re-starting it finally worked - except for three packages which I had to fix manually later..

Thanks

---

