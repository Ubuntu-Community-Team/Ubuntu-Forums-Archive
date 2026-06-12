---
title: "Problem updating from Ubuntu 9.10 to 12.04"
date: 2015-08-12
forum: Installation &amp; Upgrades
---

### Post by cleiton-xavier on 2015-08-12
Hello, I just installed a Karmic Koala in an old pc. (I don't have a cd of a newer version) and then, knowing that there is no support for such an old version, I used update-manager to try to update it, but received the following error message when executing it:

> extracting 'precise.tar.gz'
authenticate 'precise.tar.gz' against 'precise.tar.gz.gpg' 
Traceback (most recent call last):  File "/tmp/tmpdhPOFw/precise", line 3, in <module>
    from DistUpgradeMain import main
  File "/tmp/tmpdhPOFw/DistUpgradeMain.py", line 54, in <module>
    from DistUpgradeController import DistUpgradeController
  File "/tmp/tmpdhPOFw/DistUpgradeController.py", line 37, in <module>
    from utils import (country_mirror, 
  File "/tmp/tmpdhPOFw/utils.py", line 28, in <module>
    apt_pkg.init_config()
AttributeError: 'module' object has no attribute 'init_config' 

Any ideas of how to fix it?

---

### Post by howefield on 2015-08-13
Is their something stopping you from downloading a current iso and creating a live media (dvd / usb) ?

You would probably get better results doing that than going through so many stages between 9.10 and current.

---

### Post by Skaperen on 2015-08-13
can the old pc boot from USB?

---

### Post by grahammechanical on 2015-08-13
What did you do to get Update Manager to update 9.10? It would be helpful to know the process that you are working through.

As an experiment I, not so long ago,  decided to install a very old version of Ubuntu and then upgrade it all the way to the latest Ubuntu. I think I started with a version older than 9.10 but the user interface became unusable with the upgrade from 10.10 to 11.04. The UI became a mixture of Gnome 2 panel and Unity. And it did not look good. The screen colours were all messed up.

I would not recommend trying anything like that. But if you just want the learning experience then there is this,

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

But I advise to first think about the fact the 12.04 is still supported but time is running out. And if that machine cannot effectively run Ubuntu 14.04 then at some point it might be better to install Xubuntu or Lubuntu or Ubuntu Mate. And it might make sense to do that now.

Regards.

---

### Post by davidcharlesyang on 2015-12-09
I too, get this same error. (but i'm on 9.04)

```
~$ sudo do-release-upgradeChecking for a new ubuntu release
Done Upgrade tool signature
Done Upgrade tool
Done downloading
extracting 'precise.tar.gz'
authenticate 'precise.tar.gz' against 'precise.tar.gz.gpg'
Traceback (most recent call last):
  File "/tmp/tmpPc5iv5/precise", line 3, in <module>
    from DistUpgradeMain import main
  File "/tmp/tmpPc5iv5/DistUpgradeMain.py", line 54, in <module>
    from DistUpgradeController import DistUpgradeController
  File "/tmp/tmpPc5iv5/DistUpgradeController.py", line 37, in <module>
    from utils import (country_mirror,
  File "/tmp/tmpPc5iv5/utils.py", line 28, in <module>
    apt_pkg.init_config()
AttributeError: 'module' object has no attribute 'init_config'

```

I wanted to use this old powermac g5 as a server, tried 14.xx (i don't remember), installed, but was not bootable. Researching a little bit, found most of the most recent versions had issues with the bootloader. Some mentioned 9.04 worked. So installed it, and lo and behold, it works =). Thus, here I am, trying to upgrade to the most recent. unsure if [COLOR=#000000]cleiton-xavier was having the same issue as me, but advise if possible =)

[/COLOR]```
$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 9.04
Release:        9.04
Codename:       jaunty

```

---

### Post by Bucky Ball on 2015-12-09
As suggested. Do a clean install. 9.** is ancient and you are going to have a heck of job dragging it into the present. 

14.04 LTS might be best for both of you as it is a long-term support release supported until 2019 and easily upgradeable to the next LTS, 16.04 LTS (2021), via the net in the latter half of next year. 

Good luck. :)

PS: With the Mac you have to install from DVD as far as I know (but you can burn a USB and 'Try Ubuntu' from it on the Mac, just can't install). I don't know of issues with the bootloader. It is just different from a 'PC' install. You need to use reFIND from memory, and perhaps Boot Camp (which you may already have). 

You can ask about it in the ***[Apple Hardware Users]("http://ubuntuforums.org/forumdisplay.php?f=328")*** section of the forums if you need help with it. Sure some will be forthcoming. 

Depending on the specs of your machines (and this applies to both posters), which I'm presuming is fairly low-end, you may need to use a lighter flavour, Lubuntu or Xubuntu. The latest Ubuntu is absolutely nothing like 9.04 in appearance (for a start), is much bulkier and uses the Unity desktop environment. 

Either of the other two flavours I mention will look more familiar and are worth a go. The LTS releases have three years support rather than Ubuntu's five. ;)

---

### Post by QIII on 2015-12-09
What research led you to believe that there was a problem with the bootloader on recent versions?  We have an Apple Hardware Users section that might be an appropriate place to ask questions.

You would do yourself a favor if you skipped upgrading and simply installed a supported release.

---

### Post by davidcharlesyang on 2015-12-10
thanks. I'll research there =)

---

