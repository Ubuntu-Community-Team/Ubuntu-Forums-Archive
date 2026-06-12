---
title: "cannot start google earth in user account"
date: 2008-05-17
forum: Installation &amp; Upgrades
---

### Post by antony_css on 2008-05-17
I typed "sudo googleearthlinux.bin" to install the google earth.

The google earth run perfectly when I typed "sudo googleearth".
But when I typed "googleearth", only a empty window is opened. It only show me the dark background with stars shining in it that I can drag with my mouse. However, the Earth never appear.

Does google earth reads configration files only in root account? How can I solve it?

---

### Post by NightwishFan on 2008-05-17
Uninstall googleearth with the uninstall.sh script. Then add the medibuntu repositories and install it from there, it seems more stable. How to install in one command for hardy:

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list && sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update && sudo apt-get install googleearth-4.3
```

Just tested now on Hardy and it works. (Remember to accept the google earth license when it comes up.)

---

### Post by abh83 on 2008-05-17
> **NightwishFan said:**
> Uninstall googleearth with the uninstall.sh script. Then add the medibuntu repositories and install it from there, it seems more stable. How to install in one command for hardy:

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list && sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update && sudo apt-get install googleearth-4.3
```

Just tested now on Hardy and it works. (Remember to accept the google earth license when it comes up.)

I just followed your method but I can _only_ launch google earth through the terminal and with sudo

```
sudo googleearth
```

any help there?

---

### Post by abh83 on 2008-05-17
okay problem solved! i just followed gmenezesg advice off this thread: [http://ubuntuforums.org/showthread.php?t=206711](http://ubuntuforums.org/showthread.php?t=206711)

:)

---

### Post by marciowb on 2008-08-11
Thanks, Abh83!

I follow the instructions at [http://ubuntuforums.org/showpost.php?p=4831767&postcount=5](http://ubuntuforums.org/showpost.php?p=4831767&postcount=5) and now I can run Google Earth without the [COLOR="DarkRed"]sudo googleearth[/COLOR]
I just delete the following user directory:
[COLOR="DarkRed"]sudo rm -rf ~/.googleearth
sudo rm -rf ~/.config/Google[/COLOR]

Thank you,
[Marcio Wesley Borges]("http://www.marciowb.net/blog")

---

