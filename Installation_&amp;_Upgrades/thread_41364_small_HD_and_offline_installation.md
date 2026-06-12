---
title: "small HD and offline installation"
date: 2005-06-13
forum: Installation &amp; Upgrades
---

### Post by tiramisu on 2005-06-13
I want to install ubuntu onto an old machine with less than 1G harddrive and no working network connections, but a bootable CD drive. So far I have succesfully done a mimimum "server" install from CD (this takes less then 250M). My plan is to add to this a window manager (but no KDE nor GNOME which take up too much space) and a few other packages but only the bare minimum so as not to run out of space.

I have another newer machine, with a large disk and fast internet access and a free partition to experiment with ubuntu. On the newer machine, I did the same server install, activate the network and the ubuntu repositories, and am able to add the different packages that I need. Before installing any package I check with "apt-get -qq --print-uris install package" what will be fetched over the network (instead of using the install CD) and download the corresponding files with "wget". Then I copy these files on the old machine's HD (via CD). Thus I have, in principle, everything available on the old machine: either on the Ubuntu-install CD or on the local filesystem.

However there are some problems:
I can now install a package (not available on the install CD) from the local filesystem by using "dpkg -i XXX". This obviously complains about missing dependencies. So I have to manually install the dependencies and this involves a lot of trial and error to get the correct order: some of the missing packages are included in the Ubunutu CD (but are not part of the server install) and can be installed with apt-get, others have been downloaded and can be installed with "dpkg" but may involve some more dependencies. I managed to get a working AfterStep, but with a lot of hassle.
It would be nice to use the fabulous apt-get also for packages that are available on the filesystem and to let it take care of the dependencies: all the needed packages are either on the hard-drive or on the install CD.

My question is: How must apt-get be configured to look up packages on the ubuntu CD or in some specified directory? Maybe this requires some special structure or layout for the directory containing the "local repository". Any suggestions/help very welcome.

[I am new to ubuntu, but not to Linux]

---

### Post by tonym on 2005-06-13
Have a look at the apt-zip and apt-move packages.   (Both in universe).

Regards

Tony.

---

