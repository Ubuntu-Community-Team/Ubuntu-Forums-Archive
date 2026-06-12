---
title: "apt /synaptic database problem?"
date: 2006-07-03
forum: Installation &amp; Upgrades
---

### Post by marineBoy on 2006-07-03
Hi,
I've just upgraded  Kubuntu from breezy to dapper on a dell inspiron 6000 using the alternate CD. The upgrade seems to have gone OK, but there were some timeouts when it fetched a few packages from the net. 

I upgraded via the command line following the instructions in the sticky threads (sudo apt-get update && sudo apt-get dist-upgrade). At then end it listed the timed out packages and gave a couple of apt-get options to try. These didn't work. I then went into synaptic and looked for packages requiring upgrades and it lists **everything** including all the packages it successfully upgraded. It's as if synaptic doesn't recognise that the packages have been installed.  I'm on dialup so downloading the lot through synaptic isn't an option.

Any thoughts? Is there some way to make synaptic redo the database of installed packages?

Regards,

---

### Post by jrib on 2006-07-03
[QUOTE=marineBoy]Hi,
I've just upgraded  Kubuntu from breezy to dapper on a dell inspiron 6000 using the alternate CD. The upgrade seems to have gone OK, but there were some timeouts when it fetched a few packages from the net. 

I upgraded via the command line following the instructions in the sticky threads (sudo apt-get update && sudo apt-get dist-upgrade). At then end it listed the timed out packages and gave a couple of apt-get options to try. These didn't work. I then went into synaptic and looked for packages requiring upgrades and it lists **everything** including all the packages it successfully upgraded. It's as if synaptic doesn't recognise that the packages have been installed.  I'm on dialup so downloading the lot through synaptic isn't an option.

Any thoughts? Is there some way to make synaptic redo the database of installed packages?

Regards,[/QUOTE]

Maybe apt downloaded the .deb files but didn't get a chance to install them.  You can try something like 'sudo aptitude install name_of_package' (or apt-get if you want) for a package you believe is installed.  Just list them all, seperated by a space.

---

