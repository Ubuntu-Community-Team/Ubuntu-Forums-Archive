---
title: "Cannot complete update on Natty"
date: 2011-11-06
forum: Installation &amp; Upgrades
---

### Post by deskman on 2011-11-06
I have a laptop with 11.04 natty installed and update manager popped u saying that i have updates to install. when i try to download them it says that some files could not be fetched and that oneiric ocelot!!!! cd is required. so i downloaded it and inserted in the cd-rom and tried to perform update again and it failed with the same result. here is also the terminal output:

Need to get 0 B/11.5 MB of archives.
After this operation, 69.6 kB disk space will be freed.
Do you want to continue [Y/n]? y
Err cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)/ oneiric/main patch i386 2.6.1-2
  Unable to stat the mount point /media/Ubuntu\04011.10\040i386/ - stat (2: No such file or directory)
Failed to fetch cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)]/pool/main/p/patch/patch_2.6.1-2_i386.deb  Unable to stat the mount point /media/Ubuntu\04011.10\040i386/ - stat (2: No such file or directory)
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


--fix-missing didn't work too. i also noticed that in Synaptic i cannot remove any packages, the "apply" button is grey. but there is no problem to install. please help!

---

### Post by Old_Grey_Wolf on 2011-11-06
Open "Update Manager", then click the Settings button. When the setting window opens, select the "Ubuntu Software" tab. There should be a check-box for the Cdrom; uncheck the check-box. Then try to update again.

---

### Post by deskman on 2011-11-06
thanks a lot i already did something similar to what u explained here. actually i messed up things when i aborted upgrade to oneiric. this way the oneiric cd left in the sources.list

---

