---
title: "Re-installing deb packages"
date: 2008-10-08
forum: Installation &amp; Upgrades
---

### Post by swapnil on 2008-10-08
To create a backup of all the applications on Ubuntu 8.04 like Banshee, Audacity and the likes, I just copied the archives directory in "/var/cache/apt/", so that incase I goof up the system, I can reinstall the applications by using "sudo dpkg -i [filename]". I had downloaded all of them before by using the command "sudo apt-get install [program]" command.

Now, when I tried to install a particular package(after the system goof up), it showed error messages regarding installation of other package dependencies which apt had downloaded automatically. Although I managed to get the application installed through individual dpkg commands for each package and its dependencies, it was quite mundane.

I require an easy way to reinstall applications through a backup instead of downloading them again by "apt-get".

1) How can I take backups of applications and install them later?
2) How can I install these packages that I've stored without individually unpacking them?

Thanks.

---

### Post by robert shearer on 2008-10-08
You want the APToncd application that backs-up to cd your Apt cache and the dependencies are all taken care of.
Check Synaptic. I think it is there in Hardy as standard though remember having to download it as a .deb in Gutsy.

---

