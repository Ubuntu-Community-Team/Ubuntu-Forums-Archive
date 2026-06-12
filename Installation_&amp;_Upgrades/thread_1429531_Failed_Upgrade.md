---
title: "Failed Upgrade?"
date: 2010-03-14
forum: Installation &amp; Upgrades
---

### Post by LeadFingers on 2010-03-14
Ever had a failed upgrade that left you at the prompt instead of at your desktop? 

The old solution was to run ```
sudo dpkg-reconfigure xserver-xorg
``` and select a generic driver to get you to your desktop OR select "Recovery Mode" from the grub menu and use "Xfix". Sadly those options are no longer available in 9,10 but there is a solution.

Yes it's possible to use the live disk and download the correct driver but the install is tricky and the process is anything but quick.

If you have net access this solution is quick & fairly easy.

From the prompt install "Envyng"
```
sudo apt-get install envyng-core
```

After it's installed, start it in a text window
```
sudo envyng -t
``` 

this brings up a text window with the options to install either the Nvidia or the Ati drivers and lets you choose the driver.
By following the instructions and hitting a few buttons your drivers will be installed and it will ask if you want to reboot.

Yes we all love the ease of our graphical user interfaces and the command line can be daunting for the newbie but this is a 5 minute fix that doesn't require much skill. I've yet to find anything quicker or easier.

---

