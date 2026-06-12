---
title: "White screen i need to install defult graphics drivers"
date: 2009-12-04
forum: Installation &amp; Upgrades
---

### Post by acidpiper on 2009-12-04
Please can someone to tell me how to install the default graphic drivers from the recovery console as i have not backed them up and installed the ATI drivers from the ATI website
Please help

---

### Post by presence1960 on 2009-12-04
> **acidpiper said:**
> Please can someone to tell me how to install the default graphic drivers from the recovery console as i have not backed them up and installed the ATI drivers from the ATI website
Please help

Boot into recovery mode. Choose netroot (command prompt with networking). If you do not have envyng installed install it by running these commands one at a time:

```
sudo apt-get install envyng-core
sudo apt-get install envyng-qt
sudo apt-get install envyng-gtk
```

You may not need the sudo, I think you may be logged in as root in recovery mode.

Then run ```
envyng -t
```

Follow the prompts for installing your ATI driver. I would see if envy will first uninstall the one you have that is giving you the problem. If the ATI driver still gives you white screen after installing with envy reboot into recovery mode from GRUB menu and use envy to uninstall driver.

---

### Post by acidpiper on 2009-12-04
WOW! that worked first time thank you so much for your help!!! that was genius. i am now stuck with the original issue that i had i updated where it is saying that my system is running in low graphics mode, and compiz is not working and the my videos wont play (just get stills) Do you have any suggestions

Thanks again

---

### Post by presence1960 on 2009-12-05
> **acidpiper said:**
> WOW! that worked first time thank you so much for your help!!! that was genius. i am now stuck with the original issue that i had i updated where it is saying that my system is running in low graphics mode, and compiz is not working and the my videos wont play (just get stills) Do you have any suggestions

Thanks again

for vids I would uninstall gnash & swfdec. Then open a terminal and run ```
sudo apt-get install flashplugin-nonfree
``` for 32 bit & if you are running 64 bit see [here]("http://ubuntuforums.org/showthread.php?t=1259102").

Try going System > Preferences > Appearance. Choose Visual Effects tab and select custom. If everything else is OK this should activate compiz. I would also install compiz-fusion icon which will allow you to set some prefs for compiz and emerald and reload the window manmager. In terminal run sudo apt-get install fusion-icon. If not already installed you can add simple ccsm for compiz settings. In terminal run ```
sudo apt-get install simple-ccsm
```

As far as low graphics mode you will have to wait for someone else as I am not experienced in that matter. But at least you can get your vids and compiz up in the meantime.

---

