---
title: "Please help! launcher and menu gone after 13.04 upgrade"
date: 2013-05-26
forum: Installation &amp; Upgrades
---

### Post by azitizz on 2013-05-26
Hi there, I just upgraded to Ubuntu 13.04 from 12.10 on my Toshiba satellite L350D today. It seems now my launcher and menu are disabled or gone. I've been trying various solutions posted on askubuntu.com but none seem to work for my case.

Many seem to have to do with re-enabling the unity plugin etc.. in ccsm. I've tried that but curiously, the icon for the unity plugin in ccsm would display but without a checkbox beside it. 

There was a checkbox in the menu bar on the left of ccsm after clicking on the unity plugin icon, and I would check it there, but a message would display about needing to make other changes (You need to install open GL.. you need to enable Scale, requires plugin EXPO) and things would simply freeze up for a bit and it seems no changer were made and the checkbox for Unity plugin is once again unchecked...

Any other ways I can get my launcher and menu bar back up and running? thansk very much
Michael

---

### Post by sudo san on 2013-05-27
Hi,
Im not sure but unity might not have been configured correctly, Try (assuming you have access to a command line):
```
sudo dpkg-reconfigure unity
sudo dpkg --configure -a
```

Then reboot
(If unable to use GUI:
```
sudo reboot
```)

If that does not work then please post the output of:
```
sudo apt-get update -qq && sudo apt-get upgrade -s -qq
```

It might just be a simple act of correcting dependencies.

---

