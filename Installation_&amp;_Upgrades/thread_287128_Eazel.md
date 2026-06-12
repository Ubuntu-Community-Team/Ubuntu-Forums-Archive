---
title: "Eazel"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by Jerim on 2006-10-28
I started the upgrade and went to bed. My computer hibernated, which it wasn't set to do (Common problem I have had.). So I had to do the last part of the upgrade blindfolded. I just kept hitting enter until the hardrive light quit flashing. Restarted the system, and everything seemed to be good. There were a few updates I still needed to get. I installed those, and rebooted again. 

I noticed that my wireless was no longer working after the second reboot. No problem, I just need to walk through the guide I used to set it up originally. However, whenever I type "sudo apt-get install ndiswrapper-utils" I get: 

[I]Setting up gtk-engines-eazel (0.3-5.1) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing gtk-engines-eazel (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 gtk-engines-eazel
E: Sub-process /usr/bin/dpkg returned an error code (1)[/I]

So I go to the Package Manager to either reinstall gtk-engines-eazle or to remove it and reinstall. Here is what I get:
E: gtk-engines-eazel: subprocess post-installation script returned error exit status 2[/I]

After another reboot, now my Desktop icons are not viewable. When I click on Places --> Desktop it tells me:

*There is no default action associated with this location.*

I believe the desktop problem may be related. I can still access my Home and Desktop folder from a terminal. All the data is still there.

---

