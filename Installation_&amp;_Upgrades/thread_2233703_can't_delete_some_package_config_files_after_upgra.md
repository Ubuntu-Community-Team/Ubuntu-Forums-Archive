---
title: "can't delete some package config files after upgrading kernel."
date: 2014-07-10
forum: Installation &amp; Upgrades
---

### Post by strelkin2 on 2014-07-10
Hi!
Recently i upgraded kernel in my ubuntu 12.04 from 3.2 to 3.13. Now after i clean my OS with ubuntu-tweak and reboot - OS no longer boots. Since i made an image of my system partition and i made many-many tryes - i know that the cause is in one of these config files from packages that are not installed in my system now - i already cleaned them: x11-xserver-utils-lts-saucy, libegl1-mesa-drivers-lts-saucy, libopenvg1-mesa-lts-saucy, libxatracker1-lts-saucy, xserver-xorg-lts-saucy, libglapi-mesa-lts-saucy, libgl1-mesa-dri-lts-saucy, xserver-common-lts-saucy, xserver-xorg-core-lts-saucy, libegl1-mesa-lts-saucy
libgbm1-lts-saucy, libgl1-mesa-glx-lts-saucy. So if try to remove these files - the system will not boot.
Do you have any ideas why is this and how can i fix it?
Thanks in advance.

---

### Post by ibjsb4 on 2014-07-10
> i know that the cause is in one of these config files from packages that  are not installed in my system now - i already cleaned them
I have never found it necessary to remove or clean these files.

Can you revert back to the 3.2 kernel?

What error message do you get at boot?

Edit:  Don't know if will help or not.
[http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482)

---

### Post by strelkin2 on 2014-07-10
> I have never found it necessary to remove or clean these files.
it's necessary to clean as much as possible if one have 32gb ssd.
i can and i tried to go back to 3.2 but the problem persists anyway. maybe it's because of 3.11 kernel that i had after a partial distribution update after adding libreoffice ppa but now i have a different kernel and i don't have any of it's packages in os - just some config files.
i don't get any error message - it just boots and hangs so i can't even press anything like ctrl+alt+f1, but if i press the power button - computer shuts down normally - i mean it terminates works etc. just the screen remains unchanged.

> [http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482)
this utility solves problems at early boot time - not my case.

---

### Post by ibjsb4 on 2014-07-10
Time to reinstall, that will really clean things up.  Good luck :)

---

### Post by deadflowr on 2014-07-10
Maybe we need to get a better picture of how your setup was to begin with.

You had the 3.2 kernel and the xserver packages for saucy?
For the record, the 3.2 kernel series was the original kernel included on 12.04 and 12.04.1.
That setup (12.04, 12.04.1) did not include the saucy xserver packages, nor any other LTS xserver packages.

That said, do you even have any xserver packages anymore?

The 3.13 kernel series has not been added the [hardware enablement stack]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack") yet.
It will be next month when 12.04.5 is finally released.

So I don't know which xserver package you would want as of now.
But that would seem to be the main problem as of now, from what I have gathered.

Maybe you could lists which packages you do have...

---

