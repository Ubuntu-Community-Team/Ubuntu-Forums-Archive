---
title: "Upgrade from 12.04 to 12.10, blank screen on boot"
date: 2013-03-26
forum: Installation &amp; Upgrades
---

### Post by MattRussellUK on 2013-03-26
I upgraded my laptop (a Dell Vostro) from Ubuntu 12.04 to 12.10, and now I'm getting a blank screen on boot. If I boot in recovery mode, I can get to a command prompt. I had a look at /var/log/Xorg.log. It failed saying "no screens found", and "No drivers available". It tried intel, vesa, modesetting and fbdev, within messages like:

'Failed to load module "intel (module does not exist)"'

Snippet from lspci -v:


Intel Corp 3rd Gen Core processor Grahics Controller (rev 09) 
Subsystem: Dell Device 0562
Kernel driver in user: i915

Any help much appreciated!

---

### Post by MAFoElffen on 2013-03-26
> **MattRussellUK said:**
> I upgraded my laptop (a Dell Vostro) from Ubuntu 12.04 to 12.10, and now I'm getting a blank screen on boot. If I boot in recovery mode, I can get to a command prompt. I had a look at /var/log/Xorg.log. It failed saying "no screens found", and "No drivers available". It tried intel, vesa, modesetting and fbdev, within messages like:

'Failed to load module "intel (module does not exist)"'

Snippet from lspci -v:


Intel Corp 3rd Gen Core processor Grahics Controller (rev 09) 
Subsystem: Dell Device 0562
Kernel driver in user: i915

Any help much appreciated!
1st insure ensure  that it "is" there or not...
```

dkg -l | grep -i intel

```
The package should be "xserver-xorg-video-intel". If for some reason it's not there, install it. But...

Thinking it's there and just not working. There is a known bug last week on the current kernel in 12.10 affecting some Intel GPU's. The work-around (easiest) was to run on an earlier kernel (select from the Grub Menu) and to keep running upgrades to check for the next kernel upgrade, which should correct that.

Intel GPU support is default in kernel and Xorg... but something happened with that last kernel upgrade in 12.10. Trying the mainline kernel of that version, same, as it was an upstream problem.

---

### Post by MattRussellUK on 2013-03-26
I have xserver-xorg-video-intel-lts-quantal 2;2.20.9-0ubuntu2~precise2. dpkg --status says it's "Status: deinstall ok config-files". I've tried installing plain xserver-xorg-video-intel, but get told: "The following packages have unmet dependencies: Depends: xserver-xorg-core >= 2:1.22.99.901". I do have xserver-xorg-core-lts-quantal 2:1.13.0-0ubuntu6.1~precise2 currently installed -- do I need to somehow swap these lts-quantal packages out? Where did they come from?

---

### Post by MattRussellUK on 2013-03-26
OK, this sorted me out:

```
  sudo apt-get purge xserver-xorg-lts-quantal
  sudo apt-get purge xserver-xorg-core-lts-quantal
  sudo apt-get install xserver-xorg
```

---

### Post by eddo22 on 2014-03-18
> **MattRussellUK said:**
> OK, this sorted me out:

```
  sudo apt-get purge xserver-xorg-lts-quantal
  sudo apt-get purge xserver-xorg-core-lts-quantal
  sudo apt-get install xserver-xorg
```


That worked for me, thank you!

---

